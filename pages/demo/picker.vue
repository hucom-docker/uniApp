<template>
    <view class="mvpue-picker">
        <view class="page-hd">
            <view class="page-title">mvpue-picker 示例</view>
            <view class="page__desc">选中的值:</view>
            <view class="picker-text">{{pickerText}}</view>
        </view>
        <view class="page-bd">
            <button type="default" @click="showSinglePicker">单列选择</button>
            <button type="default" @click="showTimePicker">时间选择</button>
            <button type="default" @click="showMulPicker">多列选择</button>
            <button type="default" @click="showMulLinkageTwoPicker">二级联动选择</button>
            <button type="default" @click="showMulLinkageThreePicker">三级联动选择</button>
        </view>
        <mpvue-picker ref="mpvuePicker" :mode="mode" :deepLength=deepLength :pickerValueDefault="pickerValueDefault" @onChange="onChange"
            @onConfirm="onConfirm" @onCancel="onCancel" :pickerValueArray="pickerValueArray"></mpvue-picker>
    </view>
</template>

<script>
    import mpvuePicker from '../../components/picker/index.vue';

    export default {
        components: {
            mpvuePicker
        },
        data() {
            return {
                mode: 'selector',
                deepLength: 0, // 几级联动
                pickerValueDefault: [], // 初始化值
                pickerValueArray: [], // picker 数组值
                pickerText: '',
                pickerSingleArray: [{
                        label: '1号~7号',
                        value: '1号~7号'
                    },
                    {
                        label: '8号~15号',
                        value: '8号~15号'
                    },
                    {
                        label: '16号~23号',
                        value: '8号~15号'
                    },
                    {
                        label: '24号~31号',
                        value: '8号~15号'
                    }
                ],
                pickerMulArray: [
                    [{
                            label: '中国',
                            value: 1
                        },
                        {
                            label: '美国',
                            value: 2
                        },
                        {
                            label: '日本',
                            value: 3
                        },
                        {
                            label: '俄罗斯',
                            value: 4
                        }
                    ],
                    [{
                            label: '茶',
                            value: 1
                        },
                        {
                            label: '咖啡',
                            value: 2
                        },
                        {
                            label: '寿司',
                            value: 3
                        },
                        {
                            label: '奶酪',
                            value: 4
                        }
                    ],
                    [{
                            label: '歼20',
                            value: 1
                        },
                        {
                            label: 'F22',
                            value: 2
                        },
                        {
                            label: '秋月级',
                            value: 3
                        },
                        {
                            label: 'T50',
                            value: 4
                        }
                    ]
                ],
                mulLinkageTwoPicker: [{
                        label: '飞机票',
                        value: 0,
                        children: [{
                                label: '经济舱',
                                value: 1
                            },
                            {
                                label: '商务舱',
                                value: 2
                            }
                        ]
                    },
                    {
                        label: '火车票',
                        value: 1,
                        children: [{
                                label: '卧铺',
                                value: 1
                            },
                            {
                                label: '坐票',
                                value: 2
                            },
                            {
                                label: '站票',
                                value: 3
                            }
                        ]
                    },
                    {
                        label: '汽车票',
                        value: 3,
                        children: [{
                                label: '快班',
                                value: 1
                            },
                            {
                                label: '普通',
                                value: 2
                            }
                        ]
                    }
                ],
                mulLinkageThreePicker: [{
                        label: 'phone',
                        value: 0,
                        children: [{
                                label: 'iphone',
                                value: 1,
                                children: [{
                                        label: 'iphoneX',
                                        value: 1
                                    },
                                    {
                                        label: 'iphone8',
                                        value: 2
                                    },
                                    {
                                        label: 'iphone8 Plus',
                                        value: 3
                                    }
                                ]
                            },
                            {
                                label: 'android',
                                value: 1,
                                children: [{
                                        label: 'vivo',
                                        value: 1
                                    },
                                    {
                                        label: '魅族',
                                        value: 2
                                    },
                                    {
                                        label: '小米',
                                        value: 3
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        label: 'PC',
                        value: 0,
                        children: [{
                                label: 'mac',
                                value: 1,
                                children: [{
                                        label: 'macbook Pro',
                                        value: 1
                                    },
                                    {
                                        label: 'iMac',
                                        value: 2
                                    },
                                    {
                                        label: 'mackbook',
                                        value: 3
                                    },
                                    {
                                        label: 'mackbook air',
                                        value: 3
                                    }
                                ]
                            },
                            {
                                label: 'windows',
                                value: 1,
                                children: [{
                                        label: 'dell',
                                        value: 1
                                    },
                                    {
                                        label: 'surface',
                                        value: 2
                                    },
                                    {
                                        label: 'thinkpad',
                                        value: 3
                                    }
                                ]
                            }
                        ]
                    }
                ]
            };
        },
        methods: {
            onChange(e) {
                console.log(e);
            },
            onCancel(e) {
                console.log(e);
            },
            // 单列
            showSinglePicker() {
                this.pickerValueArray = this.pickerSingleArray;
                this.mode = 'selector';
                this.pickerValueDefault = [];
                this.$refs.mpvuePicker.show();
            },
            // 时间选择
            showTimePicker() {
                this.mode = 'timeSelector';
                this.pickerValueDefault = [1, 2];
                this.$refs.mpvuePicker.show();
            },
            // 多列选择
            showMulPicker() {
                this.pickerValueArray = this.pickerMulArray;
                this.mode = 'multiSelector';
                this.pickerValueDefault = [1, 1, 1];
                this.$refs.mpvuePicker.show();
            },
            // 二级联动选择
            showMulLinkageTwoPicker() {
                this.pickerValueArray = this.mulLinkageTwoPicker;
                this.mode = 'multiLinkageSelector';
                this.deepLength = 2;
                this.pickerValueDefault = [1, 0];
                this.$refs.mpvuePicker.show();
            },
            // 三级联动选择
            showMulLinkageThreePicker() {
                this.pickerValueArray = this.mulLinkageThreePicker;
                this.mode = 'multiLinkageSelector';
                this.deepLength = 3;
                this.pickerValueDefault = [1, 1, 1];
                this.$refs.mpvuePicker.show();
            },
            showPickerView() {
                this.$refs.mpvuePicker.show();
            },
            onConfirm(e) {
                console.log(e);
                if (this.mode === 'selector') {
                    this.pickerText = e.label;
                } else if (this.mode === 'timeSelector') {
                    this.pickerText = e.label;
                } else if (this.mode === 'multiSelector') {
                    this.pickerText = e.label;
                } else if (
                    this.mode === 'multiLinkageSelector' &&
                    this.deepLength === 2
                ) {
                    this.pickerText = e.label;
                } else if (
                    this.mode === 'multiLinkageSelector' &&
                    this.deepLength === 3
                ) {
                    this.pickerText = e.label;
                }
            }
        }
    };
</script>

<style>
    .page-hd {
        padding: 80rpx;
    }

    .page-title {
        font-size: 40rpx;
        font-weight: 800rpx;
    }

    .page-bd {
        padding: 30rpx;
    }

    .picker-text,
    .page__desc {
        margin-top: 20rpx;
    }

    button {
        margin-top: 30rpx;
    }
</style>
