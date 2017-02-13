<template>
  <div>
    <div class="ui accordion project-bz">
      <div class="form-style-bz">
        <div @click="project_is_open=!project_is_open" :class="{'active-bz': !project_is_open}" class="title application-title-bz">
          <div :class="{'active-bz': !project_is_open}" class="form-number-color-bz">1</div>
          <p>所属项目</p>
        </div>
        <div class="content form-content-bz">
          <a v-for="data in projects" href="javascript:;"><p>{{data}}</p></a>
        </div>
      </div>
    </div>
    <div class="ui accordion type-bz">
      <div class="form-style-bz">
        <div @click="type_is_open=!type_is_open" :class="{'active-bz': !type_is_open}" class="title application-title-bz">
          <div :class="{'active-bz': !type_is_open}" class="form-number-color-bz">2</div>
          <p>外包类型</p>
        </div>
        <div class="content form-content-bz">
          <a v-for="data in types" href="javascript:;"><p>{{data}}</p></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import $ from 'jquery'
  export default {
    props: {
    },
    components: {
    },
    data: function () {
      return {
        projects: [
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'IN HOUSE网帆内部工作',
          'NEW BUSINESS(yansen组)',
          'NEW BUSINESS(swiss组)',
          'NEW BUSINESS(聪聪组)',
          '科莱丽CXM开发',
          '2016科莱丽日常',
          'Tiger(阳狮)'
        ],
        types: [
          '媒介/KOL',
          '视频/动画',
          '设计/插画',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '技术开发',
          '其他'
        ]
      }
    },
    mounted: function () {
      this.$nextTick(function () {
        let self = this
        // project
        this.project_accordion = $(this.$el).find('.project-bz').accordion({
          onChange: function () {
            $(window).scrollTop(0)
            self.checkProjectFixed()
            self.checkTypeFixed()
          }
        })

        this.project_accordion.accordion('open', 0)

        // type
        this.type_accordion = $(this.$el).find('.type-bz').accordion({
          onChange: function () {
            self.checkProjectFixed()
            self.checkTypeFixed()
          }
        })
        this.type_accordion.accordion('open', 0)
      })
    },
    methods: {
      checkProjectFixed: function () {
        let title = this.project_accordion.find('.title')

        title.visibility(
          {
            once: false,
            onTopPassed: function () {
              title.addClass('fixed')
            },
            onTopPassedReverse: function () {
              title.removeClass('fixed')
            }
          }
        )
      },
      checkTypeFixed: function () {
        let title = this.type_accordion.find('.title')

        title.visibility(
          {
            once: false,
            onTopPassed: function () {
              title.addClass('fixed')
            },
            onTopPassedReverse: function () {
              title.removeClass('fixed')
            }
          }
        )
      },
      select_project: function (data) {
        this.out_work.project = data
        this.project_accordion.accordion('close', 0)
        this.project_is_open = !this.project_is_open
      },
      select_type: function (data) {
        this.out_work.out_work_type = data
        this.type_accordion.accordion('close', 0)
        this.type_is_open = !this.type_is_open
      }
    }
  }
</script>

<style>
  .fixed {
    top: 0px;
    z-index: 9;
    position: fixed;
    width: 100%;
  }
  .fixed-two {
    top: 5rem;
    z-index: 9;
    position: fixed;
    width: 100%;
  }
  /*========下拉列表==========*/
  .application-title-bz {
    height: 4rem;
    background-color: #E2C4A9;
    color: #ffffff!important;
    padding: 1rem 1.5rem!important;
    font-size: 1.3rem!important;
    font-family: 'GothamHTF-Book','Arial','PingFang-SC-Regular','Droid Sans','Microsoft YaHei','san-serif';
  }
  .application-title-bz p {
    display: inline-block;
    line-height: 2rem;
    margin-left: 0.5rem;
    margin-bottom: 0rem;
  }
  .application-title-bz img {
    width: 1rem;
    height: 1rem;
    margin-top: 0.5rem;
    float: right;
  }  
  .application-title-bz.active-bz {
    background-color: #F9FCFF;
    color: #E2C4A9!important;
  }
  .form-number-color-bz.active-bz{
    background-color: #E2C4A9;
    color: #F9FCFF;
  }
  .form-number-color-bz {
    width: 1.9rem;
    height: 1.9rem;
    line-height: 1.97rem;
    font-size: 1rem;
    border-radius: 50%;
    background-color: #ffffff;
    color: #E2C4A9;
    text-align: center;
    vertical-align: middle;
    display: inline-block;
  }
  .form-number-bz {
    width: 1.9rem;
    height: 1.9rem;
    line-height: 1.97rem;
    font-size: 1rem;
    border-radius: 50%;
    text-align: center;
    vertical-align: middle;
    display: inline-block;
    background-color: #E2C4A9;
    color: #ffffff;
  }
  .application-title-bz i.icon {
    float: right;
    line-height: 2rem;
  }
  .application-title-bz i.icon.plus {
    color: #9096A2;
  }
  .ui.accordion:not(.styled) .title~.content:not(.ui).form-content-bz {
    background-color: #ffffff;
    color: #373839;
    padding-left: 1.5rem;
    padding-right: 0rem;
  }
  .form-content-bz p {
    border-bottom: 1px solid #E1E7EB;
    padding: 1.5rem 0rem;
    color: #373839;
  }
  .form-content-bz a:last-child p {
    border-bottom: none;
  } 
  .form-style-bz {
    margin-top: 1rem;
    box-shadow: 0 2px 8px 0 rgba(45,46,70,0.16);
  }
  .ui.accordion:nth-child(2) .form-style-bz {
    margin-top: 0;
  }
  .accordion-content {
    background-color: #fff;
    padding: 1.5rem 1rem;
    box-shadow: 0 2px 4px 0 rgba(44,45,69,0.10);
  }
</style>
