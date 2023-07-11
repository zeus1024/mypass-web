<!-- 外出申请页面 -->
<template>
  <div id="apply">
    <!-- <van-nav-bar title="外出申请"
                 left-text="返回"
                 safe-area-inset-top
                 fixed
                 placeholder>
      <template #left>
        <van-icon name="cross"
                  size="18" />
      </template>
      <template #right>
        <span style="font-size: 18px">...</span>
      </template>
    </van-nav-bar> -->
    <div>
      <div class="greyText">申请流程</div>
      <div class="applyProcess rowBox">
        <div class="rowBox">
          <img src="../../assets/img/true.png" />
          <p>提交</p>
          <span>——</span>
        </div>
        <div class="rowBox">
          <img src="../../assets/img/true.png" />
          <p>院级审批</p>
          <span>——</span>
        </div>
        <div class="rowBox">
          <img src="../../assets/img/true.png" />
          <p>校级审批</p>
        </div>
      </div>
    </div>
    <div>
      <div class="greyText">外出信息</div>
      <!-- 开始日期 -->
      <van-cell
        :value="startDate"
        @click="showStartDate = true"
        value-class="valueText"
      >
        <!-- 使用 title 插槽来自定义标题 -->

        <template #title>
          <span class="bt">*</span>
          <span class="custom-title">开始日期</span>
        </template>
        <template #right-icon>
          <span style="color: #2095fe; margin-left: 10px">选择</span>
        </template>
      </van-cell>
      <van-calendar v-model="showStartDate" @confirm="onConfirmStartDate" />
      <!-- 结束日期 -->
      <van-cell
        :value="endDate"
        @click="showEndDate = true"
        value-class="valueText"
      >
        <!-- 使用 title 插槽来自定义标题 -->

        <template #title>
          <span class="bt">*</span>
          <span class="custom-title">结束日期</span>
        </template>
        <template #right-icon>
          <span style="color: #2095fe; margin-left: 10px">选择</span>
        </template>
      </van-cell>
      <van-calendar v-model="showEndDate" @confirm="onConfirmEndDate" />

      <!-- 外出地点 -->
      <van-cell style="padding-left: 9px">
        <van-field
          v-model="place"
          required
          label=" 外出地点"
          label-class="labelText"
          placeholder="请具体填写到区/县"
          input-align="right"
        ></van-field>
      </van-cell>
      <!-- 外出事由 -->
      <van-cell>
        <template #title>
          <span class="bt">*</span>
          <span class="custom-title">外出事由</span>
        </template>
      </van-cell>
      <van-cell>
        <van-field
          v-model="message"
          rows="3"
          type="textarea"
          placeholder=""
          style="border: 1px solid #efefef"
        />
      </van-cell>
    </div>
    <div>
      <div class="greyText">我的信息</div>
      <van-cell title="姓名" value="张三" value-class="valueText" />
      <van-cell title="学号" value="202005201314" value-class="valueText" />
      <van-cell title="学院" value="土木与交通学院" value-class="valueText" />
      <van-cell title="年级" value="2020级" value-class="valueText" />
      <van-cell title="人员类型" value="本科生" value-class="valueText" />
    </div>
    <div>
      <div class="greyText">
        温馨提示：每次只能发起一次外出申请，外出申请生效期间内无法再次发起申请。
      </div>
    </div>
    <!-- 已批准 -->
    <div>
      <img class="pass" src="../../assets/img/pass.png" />
    </div>
    <div></div>
  </div>
</template>

<script>
export default {
  name: "apply",
  data() {
    return {
      startDate: "",
      showStartDate: false,
      endDate: "",
      showEndDate: false,
      place: "广东省广州市华南理工大学天河区五山街道五山校区北区",
    };
  },
  mounted() {},
  methods: {
    formatDate(date) {
      return `${date.getFullYear()}-${date.getMonth() + 1}-${date.getDate()}`;
    },
    onConfirmStartDate(startDate) {
      this.showStartDate = false;
      this.startDate = this.formatDate(startDate);
    },
    onConfirmEndDate(endDate) {
      this.showEndDate = false;
      this.endDate = this.formatDate(endDate);
    },
  },
};
</script>

<style>
#apply {
  background-color: #eeeeee;
  height: 100%;
}

.greyText {
  color: gray;
  padding: 16px;
}

.applyProcess {
  background-color: #fff;
  padding: 16px;
}

.rowBox {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.applyProcess img {
  width: 21px;
  height: 21px;
  margin: 0 5.2px;
  position: relative;
}

.applyProcess p {
  display: inline-block;
  color: #7f7f7f;

  margin: 0;
  padding: 0;
}

.applyProcess span {
  color: #7f7f7f;
  margin: 0.1rem;
}

.bt {
  color: red;
  font-weight: 700;
  margin-right: 5px;
}

.valueText {
  color: black;
}

.labelText {
  color: black;
  margin-right: 100px;
}

.pass {
  position: fixed;
  top: 15%;
  left: 10%;
  width: 80%;
  z-index: 10;
}
</style>
