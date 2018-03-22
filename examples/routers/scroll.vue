<template>
<div>
    <Scroll :on-reach-edge="loadData">
        <Table border ref="selection" :columns="columns4" :data="data1"></Table>
    </Scroll>
    <Button @click="handleSetData" style="position:relative; z-index: 1000">Set Data</Button>
    <Button @click="handleClearData">Clear Data</Button>
    <Button @click="handleSelectAll(true)">Set all selected</Button>
    <Button @click="handleSelectAll(false)">Cancel all selected</Button>
</div>
</template>
<script>
    export default {
        data () {
            return {
                list: [1,2,3,4,5,6,7,8,9,10],
                columns4: [
                    {
                        type: 'selection',
                        width: 60,
                        align: 'center'
                    },
                    {
                        title: 'Name',
                        key: 'name'
                    },
                    {
                        title: 'Age',
                        key: 'age'
                    },
                    {
                        title: 'Address',
                        key: 'address'
                    }
                ],
                data1: [

                ]
            }
        },
        methods: {
            loadData (dir) {
                return new Promise(resolve => {
                    setTimeout(() => {
                        if (dir > 0) {
                            const first = this.list[0];
                            for (let i = 1; i < 11; i++) {
                                this.list.unshift(first - i);
                            }
                        } else {
                            const last = this.list[this.list.length - 1];
                            for (let i = 1; i < 11; i++) {
                                this.list.push(last + i);
                            }
                        }
                        resolve();
                    }, 500);
                });
            },
            handleSelectAll (status) {
                this.$refs.selection.selectAll(status);
            },
            handleSetData () {
                this.data1 = [
                    {
                        name: 'John Brown',
                        age: 1,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 2,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 3,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 4,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    },
                    {
                        name: 'John Brown',
                        age: 5,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 6,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 7,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 8,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    },
                    {
                        name: 'John Brown',
                        age: 9,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 10,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 11,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 12,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ];
            },
            handleClearData () {
                this.data1 = [];
            },
            refresh () {
                console.log('refresh');
            },
            infinite () {
                console.log('infinite');
            }
        }
    }
</script>
<style>
    section {
        margin: 20px;
    }
    section > div {
        width: 300px;
        padding: 15px;
        margin: 5px;
        background-color: #ddf;
        border: 1px solid #446;
        border-radius: 5px;
        margin: 0 auto;
    }

    .ivu-scroll-container {
        height: 500px;
    }
</style>
