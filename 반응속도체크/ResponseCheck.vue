<template>
    <div>
        <div id="screen" :class="state" @click="onClickScreen">{{message}}</div>
        <div>
            <div>평균 시간: {{}}</div>
            <button @click="onReset">리셋</button>
        </div>
    </div>
</template>

<script>
    export default{
        data() {
            return {
                result: [],
                state: 'waiting',
                message: '클릭해서 시작',
            }
        },
        methods: {
            onReset() {

            },
            onClickScreen() {
                if (this.state ==='waiting') {
                    this.state = 'ready';
                    this.message = '초록색이 되면 클릭';
                    setTimeout(() => {
                        this.state='now';
                        this.message = '지금 클릭';
                }, Math.floor(Math.random() * 1000) + 2000);
                } else if (this.state === 'ready') {
                    clearTimeout(timeout);
                    this.state = 'now';
                    this.message = '너무 성급';
                } else if (this.state === 'now') {
                    this.state = 'waiting';      
                    this.message = '클릭해서 시작하세요';
                    this.result.push(endTime - startTime);
                }
            }
        },
    };
</script>

<script>
</script>

<style scoped>
    #screen {
        width: 300px;
        height: 300px;
        text-align: center;
        user-select: none;
    }
    #screen.waiting {
        background-color: aqua;
    }
    #screen.ready {
        background-color: red;
        color: white;
    }
    #screen.now {
        background-color: greenyellow;
    }
</style>