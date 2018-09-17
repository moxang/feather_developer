<style>
header {
  background: #515a6e;
  padding: 24px 50px;
  height: 50px;
  /* line-height: 100px; */
  width: 100%;
  text-align: center;
  padding-left: 0;
}
.layout-content[data-v-6f1839a2] {
  background: #0f8de9;
  min-height: 120px;
  line-height: 120px;
}
.layout-footer[data-v-6f1839a2],
.layout-header[data-v-6f1839a2] {
  background: #7cbce9;
  color: #fff;
}
.ivu-layout-footer {
  position: fixed;
  background: #515a6e;
  padding: 24px 50px;
  /* margin-left: 0px; */
  /* color: ; */
  /* font-size: 14px; */
  width: 100%;
  /* margin-bottom: 0; */
  bottom: 0;
  text-align: center;
  /* background-color: red; */
  /* color: white; */
  /* text-align: center; */
}
.h1 {
  text-align: end;
}
</style>

<template>
<div class="layout">
    <Layout>
        <Header>
            <Row type="flex" justify="space-between">
                <Col/>
                    <img src="./logo.png" class="logo" style="width:50px; height:50px; float:left; position:fixed"/>
                <Col/>
                    <p>FORM</p>
                <Col/>
                    <h1>{{datetime}}</h1>
            </Row>
        </Header>
        <Content class="layout-content"><br><br>
            <Form :model="formItem" :label-width="100">

                <FormItem label="Select">
                    <Select v-model="formItem.select">
                        <Option value="beijing">New York</Option>
                        <Option value="shanghai">London</Option>
                        <Option value="shenzhen">Sydney</Option>
                    </Select>
                </FormItem>
                <FormItem label="Gender">
                    <RadioGroup v-model="formItem.radio">
                        <Radio label="male">Male</Radio>
                        <Radio label="female">Female</Radio>
                    </RadioGroup>
                </FormItem>
                <FormItem label="Checkbox">
                    <CheckboxGroup v-model="formItem.checkbox">
                        <Checkbox label="Eat"></Checkbox>
                        <Checkbox label="Sleep"></Checkbox>
                        <Checkbox label="Run"></Checkbox>
                        <Checkbox label="Movie"></Checkbox>
                    </CheckboxGroup>
                </FormItem>
                <!-- <FormItem label="Text">
                    <Input v-model="formItem.textarea" type="textarea" :autosize="{minRows: 2,maxRows: 5}" placeholder="Enter something..."/>
                </FormItem> -->
                <FormItem>
                    <Button type="primary" v-on:click="submit()">Submit</Button>
                    <Button style="margin-left: 8px">Cancel</Button>
                </FormItem>
            </Form>
        </Content>
        <Footer class="ivu-layout-footer">Footer</Footer>
    </Layout>
</div>
</template>
<script type="text/javascript" src="http://vuejs.org/js/vue.min.js"></script>
<script type="text/javascript" src="http://unpkg.com/iview/dist/iview.min.js"></script>
<script>
/* eslint-disable */
import axios from "axios";
export default {
  data() {
    return {
      formItem: {
        select: "",
        Gender: "male",
        checkbox: [],
        switch: true,
        date: "",
        time: "",
        slider: [20, 50],
        textarea: ""
      },
      datetime: "",
      datetime: []
    };
  },
  methods: {
    submit() {
    //   var currentDate = new Date(),
    //     day = currentDate.getDate(),
    //     month = currentDate.getMonth() + 1,
    //     year = currentDate.getFullYear();
    //   var datetime = day + "/" + month + "/" + year;
    //   console.log(datetime);
    //   this.datetime = datetime;
    console.log("submit called")
    console.log('form:',this.formItem)
    let option={
        url:'http://localhost:3031/yaan',
        method:'post',
        data:this.formItem
        }
    axios(option)
    .then((res)=>{
        console.log('res',res)
    })
    },
  },
//   mounted() {
//     this.getUnit();
//     //grab the things we need
//     const contentForm = document.getElementById('content-Form');
//     const InputInput = contentForm.querySelector('input[name=input]');
//     const SelectInput = contentForm.querySelector('input[name=select]');
//     const RadioInput = contentForm.querySelector('input[name=Radio]');
//     const CheckboxInput = contentForm.querySelector('input[name=Checkbox]');
//     const TextInput = contentForm.querySelector('input[name=Text]');
//   }
  }

</script>
