<template>
  <div id="app">
    <!-- 切换Demo -->
    <div>
      <el-button type="primary" @click="showPart(1)">Demo1</el-button>
      <el-button type="primary" @click="showPart(2)">Demo2</el-button>
      <el-button type="primary" @click="showPart(3)">Demo3</el-button>
      <el-button type="primary" @click="showPart(4)">Demo4</el-button>
      <el-button type="primary" @click="showPart(5)">summary</el-button>
    </div>
    <!-- Demo1 -->
		<div v-show="showDemoPart.demo1Show">
			<div v-show="!dateDemo1.showChild">
				<h2>自动生成基础信息(父-子）</h2>
        <span>我是女娲，我要捏一个子泰说什么让人台撒</span>
				<el-row>
          <span>xxx11</span>  
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.age" placeholder="年龄"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.name" placeholder="姓名"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.sex" placeholder="性别"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.nationality" placeholder="国籍"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.city" placeholder="所在城市"></el-input>
					</el-col>
				</el-row>
				<el-row>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.height" placeholder="身高"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.wight" placeholder="体重"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.habby" placeholder="爱好"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.language" placeholder="语言"></el-input>
					</el-col>
					<el-col :span="4">
						<el-input v-model="dateDemo1.info.languageTwice" placeholder="第二语言"></el-input>
					</el-col>
				</el-row><br>
				<el-button type="primary" @click="demo1ParentClick">生成</el-button>
			</div>
			<info
			:rows="dateDemo1"
      v-show="dateDemo1.showChild">
			</info>
		</div>
    <!-- Demo2 -->
    <div v-show="showDemoPart.demo2Show">
      <h2>聊天(子->父)</h2>
      <h2>我是父</h2>
      <span>聊天记录：{{dateDemo2.history}}</span><br>
      <span>你收到的消息：{{dateDemo2.childSay}}</span><br>
      <span>你发送的消息：</span><br>
      <el-input
        type="textarea"
        :rows="3"
        placeholder="请输入内容"
        v-model="dateDemo2.parentSay">
      </el-input>
      <el-button type="primary" @click="pSendMessage">发送</el-button>
      <demo2
        @child-told="childTold"
        :rows="dateDemo2">      
      </demo2>
    </div>
    <!-- Demo3   -->
    <div v-show="showDemoPart.demo3Show">
      <h2>兄弟组件通信（demo3,brother）</h2>
      <h3>bus.$on,bus.$emit</h3>
      <demo3>
      </demo3>
      <brother>
      </brother>
    </div>
    <!-- Demo4 -->
    <div v-show="showDemoPart.demo4Show">
      <h2>通过LocalStorage进行通信</h2>
      <demo4>
      </demo4>
      <testone>
      </testone>
      <testtwo>
      </testtwo>
    </div>
    <!-- summary -->
    <div v-show="showDemoPart.demo5Show">
      <demo5>
      </demo5>
    </div>
      
    <div>

    </div>
  </div>
</template>

<script>
import info from './components/pro'
import demo2 from './components/demo2'
import demo3 from './components/demo3'
import brother from './components/brother'
import demo4 from './components/demo4'
import testone from './components/testOne'
import testtwo from './components/testTwo'
import demo5 from './components/demo5'
export default {
  name: 'App',
  components: {
    info,
    demo2,
    demo3,
    brother,
    demo4,
    testone,
    testtwo,
    demo5
  },
  data () {
    return {
      showDemoPart: {
        demo1Show: true,
        demo2Show: false,
        demo3Show: false,
        demo4Show: false,
        demo5Show: false
      },
			dateDemo1: {
				info: {
					age: '',
					name: '',
					sex: '',
					nationality: '',
					city: '',
					height: '',
					wight: '',
					habby: '',				
					language: '',
					languageTwice: ''
				},
				infoBase: [
					{
						label: '年龄：',
						value: ''
					}, {
						label: '姓名：',
						value: ''
					}, {
						label: '性别：',
						value: ''
					}, {
						label: '国籍：',
						value: ''
					}, {
						label: '所在城市：',
						value: ''
					}, {
						label: '身高(cm)：',
						value: ''
					}, {
						label: '体重(kg)：',
						value: ''
					}, {
						label: '爱好：',
						value: ''
					}, {
						label: '语言：',
						value: ''
					}, {
						label: '第二语言：',
						value: ''
					}
				],
				showChild: false
			},
      dateDemo2: {
        childSay: '',
        parentSay: '',
        parentSayText: '',
        toldChild: '',
        history: ''
      }
    }
	},
	methods: {
    // 项目切换按钮
    showPart(num) {
      if (num === 1) {
        this.showDemoPart.demo1Show = true
        this.showDemoPart.demo2Show = false
        this.showDemoPart.demo3Show = false
        this.showDemoPart.demo4Show = false
        this.showDemoPart.demo5Show = false
        this.dateDemo1.showChild = false
        this.restDate(num)        
      } else if (num === 2) {
        this.showDemoPart.demo1Show = false
        this.showDemoPart.demo2Show = true
        this.showDemoPart.demo3Show = false
        this.showDemoPart.demo4Show = false
        this.showDemoPart.demo5Show = false
        this.restDate(num)
      } else if (num === 3) {
        this.showDemoPart.demo1Show = false
        this.showDemoPart.demo2Show = false
        this.showDemoPart.demo3Show = true
        this.showDemoPart.demo4Show = false
        this.showDemoPart.demo5Show = false
      } else if (num ===4) {
        this.showDemoPart.demo1Show = false
        this.showDemoPart.demo2Show = false
        this.showDemoPart.demo3Show = false
        this.showDemoPart.demo4Show = true
        this.showDemoPart.demo5Show = false
      } else {
        this.showDemoPart.demo1Show = false
        this.showDemoPart.demo2Show = false
        this.showDemoPart.demo3Show = false
        this.showDemoPart.demo4Show = false
        this.showDemoPart.demo5Show = true
      }
    },
    // 项目1生成按钮
		demo1ParentClick() {
			let index = 0
			for(const key in this.dateDemo1.info) {
				this.dateDemo1.infoBase[index].value = this.dateDemo1.info[key]
				index++				
			}
			this.dateDemo1.showChild = true
		},
    // 清空数据
    restDate(num) {
      if (num === 1) {
        for(const val in this.dateDemo1.info) {
          this.dateDemo1.info[val] = ''
        }
        for(const val in this.dateDemo1.infoBase) {
          this.dateDemo1.infoBase[val].value = ''
        }
      } else if (num === 2) {
        for (const val in this.dateDemo2) {
          this.dateDemo2[val] = ''
        }

      }
     
    },
    // demo2接收子传值
    childTold(date) {
      this.$set(this.dateDemo2, 'childSay', date)
      this.dateDemo2.history += ('子：' + date + '\n')
    },
    // demo2父向子传值
    pSendMessage() {
      this.dateDemo2.parentSayText = this.dateDemo2.parentSay
      this.dateDemo2.history += ('父：'+ this.dateDemo2.parentSayText + '\n')
      this.dateDemo2.parentSay = ''
    }
	}
}
</script>

<style>

</style>