<template>
    <div style="width: 100%; height: 100%;" id="parent">
        <!--        <button @click="change">{{isShow ? '打开': '关闭'}}</button>-->
        <button id="test">test</button>
        <button @click="openIframe">打开iframe</button>
        <button @click="removeIframe">关闭iframe</button>
        <!--        <iframe id="iframe-if" v-if="isShow" width="90%" height="100%" style="display: block; margin: 0 auto;" frameborder="1"></iframe>-->
        <iframe id="iframe-if" v-if="isShow" width="90%" height="100%" style="display: block; margin: 0 auto;" frameborder="1"></iframe>
    </div>
</template>
<script>
    export default {
        name: 'IFrame',
        data () {
            return {
                //isShow: true,
                //url: 'http://192.168.6.1:5050/#/bridge?tokenid=dXNlcm5hbWU9MTMwMC1sdm1zJmR0PTIwMjAxMTI2MTIyNTQ5JmNvZGU9NWY2Y2I0NzU5ZTkyNDI5Y2RkZjAwZjZhZDkzZTY3OGU=&id=X7fA7kkRrn9-TZZ_&docId=X59o00kRMbOiM72W&module=RECEIVAL&type=dbwj'
                url: 'http://203.48.27.114:6080/#/bridge?tokenid=dXNlcm5hbWU9MTMwMC1saXh5Jm9yZ2lkPTEzMDAmZ2JtPTEzMDBCMDAmZHB0aWQ9JmR0PTIwMjAxMTE4MDkxMTIxJmNvZGU9YWI5NTA0ODQ2M2VmYTdjODVhMWRlZjQyOWQyODhlY2U=&id=X7y9d-Swupkmg-LE&docId=X2MldeSw58GbOKwI&module=RECEIVAL&type=dbwj'
            };
        },
        methods: {
            removeIframe () {
                // const test = document.getElementById('test');//获取到iframe对象
                // console.log(test);
                // if (this.isIE()) {
                //     test.removeNode(true);
                // } else {
                //     test.remove();
                // }

                const frame = document.getElementById('iframe-if');//获取到iframe对象
                //const frame = $('#iframe-if');//获取到iframe对象
                console.log(2222);
                console.log(frame);
                console.log(frame.contentWindow);
                //frame.contentWindow.document.write('');//清空i frame的内容
                frame.contentWindow.close();//避免iframe内存泄漏
                if (this.isIE()) {
                    frame.removeNode(true);
                } else {
                    frame.remove();//删除iframe
                }
                console.log(this.isIE());
                if (this.isIE()) {
                    // eslint-disable-next-line
                    //CollectGarbage();//这个方法为IE下独有，做内存释放之用，这里加上可以保险一点
                    // eslint-disable-next-line
                    setTimeout(CollectGarbage(), 1);//通过setTimeout的方式调用，可能是防止上下文中的过程变量仍然有效的原因
                    console.log('回收');
                }
            },
            openIframe () {
                $('<iframe id="iframe-if" src="' + this.url + '" name="mainIFrame" scrolling="no" frameborder="1"  width="100%" height="100%"></iframe>').appendTo($('#parent'));
            },
            // change () {
            //     this.isShow = !this.isShow;
            //     if (this.isShow) {
            //         this.$nextTick(() => {
            //             //$('#iframe-if').attr('src', 'http://192.168.210.171:6050/#/bridge?module=DISPATCH&type=pre-qcwj&tokenid=dXNlcm5hbWU9dGVzdCZkdD0yMDIwMDMyNTEyMDEzNCZjb2RlPTBiOWI2YTY5YWI0ZTg3ODJhZjIxNzAwODAzYmQ4YjUy');
            //             $('#iframe-if').attr('src', 'http://192.168.6.1:5050/#/bridge?tokenid=dXNlcm5hbWU9MTMwMC1sdm1zJmR0PTIwMjAxMTI2MTIyNTQ5JmNvZGU9NWY2Y2I0NzU5ZTkyNDI5Y2RkZjAwZjZhZDkzZTY3OGU=&id=X7fA7kkRrn9-TZZ_&docId=X59o00kRMbOiM72W&module=RECEIVAL&type=dbwj');
            //         });
            //     } else {
            //         // const frame = document.getElementById('iframe-if');//获取到iframe对象
            //         // console.log(frame);
            //         // //frame.contentWindow.document.write('');//清空i frame的内容
            //         // frame.contentWindow.close();//避免iframe内存泄漏
            //         // //frame.remove();//删除iframe
            //         // // eslint-disable-next-line
            //         // CollectGarbage();//这个方法为IE下独有，做内存释放之用，这里加上可以保险一点
            //
            //     }
            // },
            isIE () {
                //https://www.cnblogs.com/liyuchen/p/7834349.html
                //https://www.cnblogs.com/xiaolanschool/p/11353566.html
                if (!!window.ActiveXObject || 'ActiveXObject' in window) {
                    return true;
                } else {
                    return false;
                }
            }
        },
        mounted () {

            window.addEventListener('message', (event) => {
                console.log('===');
                if (event.origin === 'http://192.168.210.171:6050') {
                    console.log(111);
                    console.log(event.data);
                }
            }, false);

            this.$nextTick(() => {
                //$('#iframe-if').attr('src', 'http://192.168.210.171:6050/#/bridge?module=DISPATCH&type=pre-qcwj&tokenid=dXNlcm5hbWU9dGVzdCZkdD0yMDIwMDMyNTEyMDEzNCZjb2RlPTBiOWI2YTY5YWI0ZTg3ODJhZjIxNzAwODAzYmQ4YjUy');
                $('#iframe-if').attr('src', 'http://192.168.6.1:5050/#/bridge?tokenid=dXNlcm5hbWU9MTMwMC1sdm1zJmR0PTIwMjAxMTI2MTIyNTQ5JmNvZGU9NWY2Y2I0NzU5ZTkyNDI5Y2RkZjAwZjZhZDkzZTY3OGU=&id=X7fA7kkRrn9-TZZ_&docId=X59o00kRMbOiM72W&module=RECEIVAL&type=dbwj');

            });
        }
    };
</script>