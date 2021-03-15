<template>
  <div>
    <el-card shadow="hover">
      <div slot="header" class="clearfix">
        <span><h1>Đi tìm mật khẩu ?</h1></span>
      </div>
      <div style="margin-bottom: 2%">
          Gợi ý : Đây là năm diễn ra một sự kiện lịch sử quan trọng làm thay đổi cục diện cách mạng Việt Nam?
      </div>
      <div>
        <el-input placeholder="Đáp án của bạn là ?" style="width: 20%; margin-right: 8px" v-model="pwd"></el-input>
        <el-button type="primary" @click="checkPwd">Check</el-button>
      </div>
    </el-card>
    <div style="text-align: left; margin-top: 1%;">
        <div>
          <el-button type="success" :disabled="btnDisableList[0]" icon="el-icon-search" @click="showQuestion(quizBank[0])">Câu hỏi</el-button>
          <el-button type="primary" :disabled="btnDisableList[1]" icon="el-icon-search" @click="showQuestion(quizBank[1])">Câu hỏi</el-button>
        </div>
    </div>
    <el-dialog title="Câu hỏi" :visible.sync="question">
          <p>{{questionNow.question}}</p>
          <p><el-link type="primary" :underline="false" @click="chooseAnswer(questionNow.a)">A. {{questionNow.a}}</el-link></p>
          <p><el-link type="primary" :underline="false" @click="chooseAnswer(questionNow.b)">B. {{questionNow.b}}</el-link></p>
          <p><el-link type="primary" :underline="false" @click="chooseAnswer(questionNow.c)">C. {{questionNow.c}}</el-link></p>
          <p><el-link type="primary" :underline="false" @click="chooseAnswer(questionNow.d)">D. {{questionNow.d}}</el-link></p>
    </el-dialog>
  </div>
</template>
<script>
export default {
  name: 'Dashboard',
  data () {
    return {
      pwd: '',
      tabPosition: 'left',
      question: false,
      hint: ['Gợi ý 1', 'Gợi ý 2', 'Gợi ý 3'],
      questionNow: {},
      quizBank: [
        {
          index: 0,
          title: 'Câu hỏi 1',
          question: 'Ai là người đầu tiên lên mặt trăng ?',
          a: 'sdsd',
          b: 'aa',
          c: 'we',
          d: 'dsdxxc',
          correct: 'sdsd',
          res: 'Mỹ'
        },
        {
          index: 1,
          title: 'Câu hỏi 1',
          question: 'Ai là người đầu tiên lên mặt trời ?',
          a: 'sdsd',
          b: 'aa',
          c: 'we',
          d: 'dsdxxc',
          correct: 'sdsd',
          res: 'Mỹ'
        }
      ],
      btnDisableList: [
        false, false, false
      ]
    }
  },
  methods: {
    checkPwd () {
      const msgOptions = this.pwd === '1963' ? {
        content: 'Đúng rồi nha !!!',
        title: 'Chính xác',
        type: 'success'
      } : {
        content: 'Sai rồi nha !!!',
        title: 'Sai bét',
        type: 'error'
      }

      this.$alert(msgOptions.content, msgOptions.title, {
        confirmButtonText: 'OK',
        type: msgOptions.type
      })
    },
    showQuestion (question) {
      this.question = true
      this.questionNow = question
    },
    chooseAnswer (answer) {
      this.question = false
      this.btnDisableList[this.questionNow.index] = true
      if (answer === this.questionNow.correct) {
        this.questionNow = {}
      } else {
        alert('sdsd')
      }
    }
  }
}
</script>
