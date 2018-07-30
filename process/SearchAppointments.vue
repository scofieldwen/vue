<template>
  <div class="row search-appointments">
    <div class="col-sm-offset-3 col-sm-6">

      <div class="input-group">

        <input id="SearchApts" placeholder="Search" type="text" class="form-control" aria-label="Search Appointments"
        v-model="searchTerm" />

        <div class="input-group-btn">
          <button type="button" class="btn btn-primary dropdown-toggle"
            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">排序方式: <span class="caret"></span></button>

            <ul class="dropdown-menu dropdown-menu-right">

              <li><a href="#" id="petName">宠物名称<span class="glyphicon glyphicon-ok"></span></a></li>

              <li><a href="#" id="aptDate">日期<span class="glyphicon glyphicon-ok"></span></a></li>

              <li><a href="#" id="ownerName">主人<span class="glyphicon glyphicon-ok"></span></a></li>

              <li role="separator" class="divider"></li>

              <li><a href="#" id="asc">升序<span class="glyphicon glyphicon-ok"></span></a></li>

              <li><a href="#" id="desc">降序
                <span class="glyphicon glyphicon-ok"></span></a></li>
            </ul>
        </div><!-- input-group-btn --> 
      </div><!-- input-group --> 
    </div><!-- col-sm-offset-3 --> 
  </div><!-- search-appointments -->
</template>

<script>
export default {

  name: 'SearchAppointments',
  data() {
      return {
          searchTerm: ''
      } //return
  }, //data

  watch: {
      searchTerm: function() {
          this.$emit('searchRecords', this.searchTerm);
      } //searchTerm
  } //watch

} // export
</script>