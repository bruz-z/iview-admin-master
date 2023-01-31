<template>
  <div>
    <div>
      <card shadow>
        <nobr class="head-font">设备选择：</nobr>
        <Select v-model="model" style="width:100px;margin-right: 20px">
          <Option v-for="item in deviceList" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
        <Divider style="margin: 12px 0px"/>
        <Row>
          <Col span="6">
            设备名:
            <nobr>awdadwad</nobr>
          </Col>
          <Col span="6">电池容量: {{ deviceList[0].value }}</Col>
          <Col span="6">CPU:</Col>
          <Col span="6">DRAM:</Col>
        </Row>
      </card>
      <div>
        <br>
      </div>
      <card shadow>
        <nobr class="head-font">任务选择：</nobr>
        <Select v-model="model2" style="width:100px;margin-right: 20px">
          <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
        <nobr class="head-font">基础模型选择：</nobr>
        <Select v-model="model3" style="width:100px">
          <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
        <Divider style="margin: 12px 0px"/>
        <Row>
          <Col span="4">
            计算量:
            <nobr>awdadwad</nobr>
          </Col>
          <Col span="4">参数量</Col>
          <Col span="4">存储量:</Col>
          <Col span="4">能耗:</Col>
          <Col span="4">精度:</Col>
        </Row>
      </card>
    </div>
    <div>
      <br>
    </div>
    <div>
      <card size="large">
        <p class="head-font" style="color: rgb(225,51,12)">模型压缩</p>
        <Divider style="margin: 12px 0px"/>
        <Row>
          <Col span="14">
            <Slider v-model="value1" style="margin-right: 40px" show-input></Slider>
          </Col>
          <Col span="10">
            <Button type="primary">开始压缩</Button>
          </Col>
        </Row>
        <Row>
          <Row style="margin: 20px">
            <Col span="4">计算量:
              <nobr>awdadwad</nobr>
            </Col>
            <Col span="4">col-6</Col>
            <Col span="4">参数量：</Col>
            <Col span="4">col-6</Col>
            <Col span="4">存储量：</Col>
            <Col span="4">col-6</Col>
          </Row>
          <Row style="margin: 20px 20px 150px;">
            <Col span="4">能耗：</Col>
            <Col span="4">col-6</Col>
            <Col span="4">精度：</Col>
            <Col span="4">col-6</Col>
            <Col span="4"></Col>
            <Col span="4"></Col>
          </Row>
          <Button type="primary" style="margin-left: 40%">Download</Button>
          <Button style="margin-left: 15px"> Cancel</Button>
        </Row>
      </card>
    </div>

  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      formItem: {
        任务类型: '',
        模型选择: '',
        压缩方法: '',
        压缩率: [0, 0]
      },
      cityList: [
        {
          value: 'New York',
          label: 'New York'
        },
        {
          value: 'London',
          label: 'London'
        },
        {
          value: 'Sydney',
          label: 'Sydney'
        },
        {
          value: 'Ottawa',
          label: 'Ottawa'
        },
        {
          value: 'Paris',
          label: 'Paris'
        },
        {
          value: 'Canberra',
          label: 'Canberra'
        }
      ],
      deviceList: [
        {
          value: 'Xiaomi 12',
          label: 'Xiaomi 12'
        },
        {
          value: 'Iphone 14',
          label: 'Iphone 14'
        }
      ],
      model: '',
      model2: '',
      model3: '',
      model4: '',
      value1: 25
    }
  },
  watch: {
    model: {
      handler(newVal, oldVal) {
        if (newVal !== oldVal) {
          axios.post('get-device/', {
              deviceName: newVal
          })
            .then(function (response) {
              console.log(response.data);
            })
        }
      }
    }
  },
  methods: {}
}
</script>

<style>
.head-font {
  font-weight: bold;
  font-size: 18px;
}
</style>
