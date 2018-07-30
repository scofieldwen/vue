<template>
  <div class="panel panel-primary">

    <div class="panel-heading apt-addheading"
        @click="hidepanel=!hidepanel">
      <span class="glyphicon" :class="glyphiconType"></span> 添加预约
    </div><!-- panel-heading -->

    <div class="panel-body"
        :class="{ hide: hidepanel }">

      <form class="add-appointment form-horizontal"
        @submit.prevent="requestAdd">

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="petName">宠物名称</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="petName" placeholder="宠物的名称"
            v-model="formData.petName" />
          </div><!-- col-sm-10 --> 
        </div><!-- form-group --> 

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="petOwner">宠物主人</label>
          <div class="col-sm-10">
            <input type="text" class="form-control"
              id="petOwner" placeholder="宠物的主人" 
              v-model="formData.petOwner" />
          </div><!-- col-sm-10 -->
        </div><!-- form-group --> 

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="aptDate">日期</label>
          <div class="col-sm-4">
            <input type="date" class="form-control" id="aptDate"
            v-model="formData.aptDate" />
          </div><!-- col-sm-4 --> 
          <label class="col-sm-2 control-label" htmlFor="aptTime">时间</label>
          <div class="col-sm-4">
            <input type="time" class="form-control" id="aptTime"
            v-model="formData.aptTime" />
          </div><!-- col-sm-4 --> 
        </div><!-- form-group -->

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="aptNotes">详情</label>
          <div class="col-sm-10">
            <textarea class="form-control" rows="4" cols="50"
              id="aptNotes" placeholder="预约详情"
              v-model="formData.aptNotes"></textarea>
          </div><!-- col-sm-10 --> 
        </div><!-- form-group -->

        <div class="form-group">
          <div class="col-sm-offset-2 col-sm-10">
            <button type="submit" class="btn btn-primary pull-right">添加</button>
          </div><!-- col-sm-offset-2 --> 
        </div><!-- form-group -->

      </form>
    </div><!-- panel-body -->
  </div><!-- panel-primary -->
</template>

<script>

export default {

  name: 'AddAppointments',
  data() {
      return {
          hidepanel: true,
          formData: []
      } //return
  }, //data

  methods: {
    requestAdd: function () {
      var parsedData = {
        petName: this.formData.petName,
        petOwner: this.formData.petOwner,
        aptDate: this.formData.aptDate + ' ' + this.formData.aptTime,
        aptNotes: this.formData.aptNotes
      }
      this.$emit('addRecord', parsedData);
      this.hidepanel= true;
      this.formData = [];
    } //requestAdd
  }, //methods

  computed: {
    glyphiconType: function () {
        return {
            'glyphicon-plus': this.hidepanel == true,
            'glyphicon-minus': this.hidepanel == false
        } //return
    }
  } //computed
} //default
</script>

<style scoped>

  .panel-heading {
    cursor: pointer;
  }

</style>
 