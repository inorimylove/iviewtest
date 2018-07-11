<style lang="less">
    @import './lm.less';
</style>

<template>
    <div>
        <Row>
            <Card>
                <p slot="title">
                    <Icon type="ios-list"></Icon>
                    订单查询
                </p>
                <Row>
                    <Input v-model="searchConName3" placeholder="请输入姓名搜搜..." style="width: 200px" />
                    <span  style="margin: 0 10px;"><Button type="primary" icon="search">搜索</Button></span>
                </Row>
                <Row class="lm-row">
                    <span><Button type="success" icon="android-add" @click="modal1 = true">添加</Button></span>
                    <span  style="margin: 0 10px;"><Button type="error" icon="android-remove">删除</Button></span>
                </Row>                                 
                <Row type="flex" justify="center" align="middle" class="lm-row">
                    <Table size="small" border stripe :columns="shoppingColumns" :data="shoppingData" style="width: 100%;"></Table>
                </Row>
                <Row>
                    <Page :total="100"></Page>
                </Row>               
            </Card>
        </Row>
        <Modal
            v-model="modal1"
            title="Common Modal dialog box title"
            @on-ok="ok"
            @on-cancel="cancel"
            width="50"
            >
            <Form :model="formItem"    >
                <Row :gutter="16" align="middle" type="flex" style="margin:10px 0;" >
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                </Row>
                <Row :gutter="16" align="middle" type="flex" style="margin:10px 0;" >
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                </Row>
                <Row :gutter="16" align="middle" type="flex" style="margin:10px 0;" >
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                    <Col span="3">
                        <label>购物单号</label>
                    </Col>
                    <Col span="9">
                        <Input v-model="formItem.input" placeholder="Enter something..." />
                    </Col>
                </Row>
                                                                                        
            </Form>
            <div slot="footer">
                <Row class="lm-row">
                    <span style="margin: 0 10px;"><Button type="primary" icon="android-add" >暂存</Button></span>
                    <span style="margin: 0 10px;"><Button type="success" icon="android-add" >添加</Button></span>
                    <span style="margin: 0 10px;"><Button type="error" icon="android-remove">取消</Button></span>
                </Row> 
            </div>
        </Modal>
    </div>
</template>

<script>
export default {
    name: 'argument-page',
    data () {
        return {
            modal1: false,
            formItem: {
                input: '',
                select: '',
                radio: 'male',
                checkbox: [],
                switch: true,
                date: '',
                time: '',
                slider: [20, 50],
                textarea: ''
            },
            shoppingColumns: [
                {
                    type: 'index',
                    title: '序号',
                    width: 70
                },
                {
                    type: 'selection',
                    width: 60
                },
                {
                    title: '购物单号',
                    key: 'shopping_id',
                    align: 'center'
                },
                {
                    title: '购买物品名称',
                    key: 'name',
                    align: 'center'
                },
                {
                    title: '购买时间',
                    key: 'time'
                },
                {
                    title: '查看详情',
                    key: 'show_more',
                    align: 'center',
                    render: (h, params) => {
                        return h('Button', {
                            props: {
                                type: 'text',
                                size: 'small'
                            },
                            on: {
                                click: () => {
                                    let query = {shopping_id: params.row.shopping_id};
                                    this.$router.push({
                                        name: 'shopping',
                                        query: query
                                    });
                                }
                            }
                        }, '了解详情');
                    }
                },
                {
                    title: 'Action',
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
                                        this.show(params.index);
                                    }
                                }
                            }, '查看'),
                            h('Button', {
                                props: {
                                    type: 'warning',
                                    size: 'small'
                                },
                                on: {
                                    click: () => {
                                        this.edit(params.index);
                                    }
                                }
                            }, '修改')
                        ]);
                    }
                }
            ],
            shoppingData: [
                {
                    shopping_id: 100001,
                    name: '《vue.js实战》',
                    time: '2017年11月12日'
                },
                {
                    shopping_id: 100002,
                    name: '面包',
                    time: '2017年11月5日'
                },
                {
                    shopping_id: 100003,
                    name: '咖啡',
                    time: '2017年11月8日'
                },
                {
                    shopping_id: 100004,
                    name: '超级豪华土豪金牙签',
                    time: '2017年11月9日'
                },
                {
                    shopping_id: 100005,
                    name: '《vue.js实战》',
                    time: '2017年11月12日'
                },
                {
                    shopping_id: 100006,
                    name: '面包',
                    time: '2017年11月5日'
                },
                {
                    shopping_id: 100007,
                    name: '咖啡',
                    time: '2017年11月8日'
                },
                {
                    shopping_id: 100008,
                    name: '面包',
                    time: '2017年11月5日'
                },
                {
                    shopping_id: 100009,
                    name: '咖啡',
                    time: '2017年11月8日'
                },
                {
                    shopping_id: 100010,
                    name: '超级豪华土豪金牙签',
                    time: '2017年11月9日'
                }
            ]
        };
    },
    methods: {
        // ok () {
        //     this.$Message.info('Clicked ok');
        // },
        // cancel () {
        //     this.$Message.info('Clicked cancel');
        // }
    }
};
</script>
