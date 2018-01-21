<template>
    <div class="animate fadeIn" >
        <Row>
            <Col :sm="24" :md="24" :lg="12">
                <h3>好好学习</h3>

            <Table :columns="columns" :data="data1">
            </Table>
            </Col>
        </Row>
    </div>
</template>
<script>

    export default {
        data() {
            return{
                columns: [
                    {
                        title:'ID',
                        key: 'id'
                    },
                    {
                        title:'姓名',
                        key: 'name'
                    },
                    {
                        title: '性别',
                        key: 'sex'
                    },
                    {
                        title: '年龄',
                        key: 'age'
                    },
                    {
                        title: '地址',
                        key: 'address',
                        width: 200,
                    },
                    {
                        title: '操作',
                        key: 'action',
                        width: 150,
                        align: 'center',
                        render: (h, params) => {
                            return h('div', [

                                h('Button', {
                                    props: {
                                        type: 'primary',
                                        size: 'small'
                                    },
                                    style: {
                                        marginRight: '5px'
                                    },
                                    on: {
                                        click: () => {
                                            this.show(params.index)
                                        }
                                    }

                                },'查看'),

                                h('Button', {
                                    props: {
                                        type: 'alert',
                                        size: 'small'
                                    },
                                    on: {
                                        click: () => {
                                            this.remove(params.index)
                                        }
                                    }
                                }, '删除')
                            ]);
                        }
                    }
                ],
                data1: [
                    {
                        id: '1',
                        name: 'jfgois',
                        sex: '男',
                        age: '23',
                        address: 'djlfjhoehfoisehhioghrhgui',
                    },
                    {
                        id: '2',
                        name: '哥ois',
                        sex: '男',
                        age: '2g',
                        address: 'djlfjhoehfoisehhioghrhgui',
                    },
                    {
                        id: '3',
                        name: 'adljfis',
                        sex: '男',
                        age: '23',
                        address: 'djlfjhoehfoisehhioghrhgui',
                    },
                    {
                        id: '4',
                        name: 'jlgidjlris',
                        sex: '男',
                        age: '23',
                        address: 'djlfjhoehfoisehhioghrhgui',
                    }
                ]
            }
        },
        methods: {
            show(index) {
                this.$Modal.info({
                    title: '用户信息',
                    content: `id: ${this.data1[index].id} <br> 姓名：${this.data1[index].name}<br> 性别: ${this.data1[index].sex}<br>` +
                    `年龄: ${this.data1[index].age}<br>地址: ${this.data1[index].address}`,
                })
            },
            remove(index){
                this.data1.splice(index,1);
            }
        }
    }
</script>