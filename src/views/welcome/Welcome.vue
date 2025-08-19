<script setup lang="ts">
defineOptions({
  name: 'WelcomeWorkplace'
})

const currentUser = {
  avatar: 'https://gw.alipayobjects.com/zos/rmsportal/BiazfanxmamNRoxxVxka.png',
  name: '吴彦祖',
  userid: '0925',
  email: 'yuanguangji@3sbio.com',
  signature: '海纳百川，有容乃大',
  title: '工程师',
  group: '沈阳三生制药-信息技术部-研发部'
}

const projectNotice = [
  {
    id: 'xxx1',
    title: '财务',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/WdGqmHpayyMjiEhcKoVE.png',
    description: '那是一种内在的东西，他们到达不了，也无法触及的',
    updatedAt: '几秒前',
    member: '科学搬砖组',
    href: '',
    memberLink: ''
  },
  {
    id: 'xxx2',
    title: '采购',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/zOsKZmFRdUtvpqCImOVY.png',
    description: '希望是一个好东西，也许是最好的，好东西是不会消亡的',
    updatedAt: '6 年前',
    member: '全组都是吴彦祖',
    href: '',
    memberLink: ''
  },
  {
    id: 'xxx3',
    title: '商务',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/dURIMkkrRFpPgTuzkwnB.png',
    description: '城镇中有那么多的酒馆，她却偏偏走进了我的酒馆',
    updatedAt: '几秒前',
    member: '中二少女团',
    href: '',
    memberLink: ''
  },
  {
    id: 'xxx4',
    title: 'IT',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/sfjbOqnsXXJgNCjCzDBL.png',
    description: '那时候我只会想自己想要什么，从不想自己拥有什么',
    updatedAt: '6 年前',
    member: '程序员日常',
    href: '',
    memberLink: ''
  },
  {
    id: 'xxx5',
    title: '人事',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/siCrBXXhmvTQGWPNLBow.png',
    description: '凛冬将至',
    updatedAt: '6 年前',
    member: '高逼格设计天团',
    href: '',
    memberLink: ''
  },
  {
    id: 'xxx6',
    title: '研发',
    logo: 'https://gw.alipayobjects.com/zos/rmsportal/kZzEzemZyKLKFsojXItE.png',
    description: '生命就像一盒巧克力，结果往往出人意料',
    updatedAt: '6 年前',
    member: '骗你来学计算机',
    href: '',
    memberLink: ''
  }
]

onMounted(() => {})

onBeforeUnmount(() => {})
</script>

<template>
  <div>
    <div class="pageHeaderContent bg-white p-4 radius-md mb-4 rounded-md">
      <div class="avatar">
        <a-avatar size="large" :src="currentUser.avatar" />
      </div>
      <div class="content">
        <div class="contentTitle">
          早安，
          {{ currentUser.name }}
          ，祝你开心每一天！
        </div>
        <div>{{ currentUser.title }} |{{ currentUser.group }}</div>
      </div>
    </div>

    <a-row :gutter="24" class="mb-4">
      <a-col :xl="24" :lg="24" :md="24" :sm="24" :xs="24">
        <a-card
          class="projectList mb-2 !rounded-md"
          title="我的看板"
          :bordered="false"
          :loading="false"
          :body-style="{ padding: 0 }"
        >
          <!-- <template #extra>
            <router-link to="/"> 全部项目 </router-link>
          </template> -->
          <a-card-grid v-for="item in projectNotice" :key="item.id" class="projectGrid">
            <a-card :body-style="{ padding: 0 }" style="box-shadow: none" :bordered="false">
              <a-card-meta :description="item.description" class="w-full">
                <template #title>
                  <div class="cardTitle">
                    <a-avatar size="small" :src="item.logo" />
                    <router-link :to="item.href">
                      {{ item.title }}
                    </router-link>
                  </div>
                </template>
              </a-card-meta>
              <div class="projectItemContent">
                <router-link :to="item.memberLink">
                  {{ item.member || '' }}
                </router-link>
                <span class="datetime" ml-2 :title="item.updatedAt">
                  {{ item.updatedAt }}
                </span>
              </div>
            </a-card>
          </a-card-grid>
        </a-card>
      </a-col>
    </a-row>
  </div>
</template>

<style scoped lang="less">
.textOverflow() {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  word-break: break-all;
}

// mixins for clearfix
// ------------------------
.clearfix() {
  zoom: 1;
  &::before,
  &::after {
    display: table;
    content: ' ';
  }
  &::after {
    clear: both;
    height: 0;
    font-size: 0;
    visibility: hidden;
  }
}

.activitiesList {
  padding: 0 24px 8px 24px;
  .username {
    color: var(--text-color);
  }
  .event {
    font-weight: normal;
  }
}

.pageHeaderContent {
  display: flex;
  .avatar {
    flex: 0 1 72px;
    & > span {
      display: block;
      width: 72px;
      height: 72px;
      border-radius: 72px;
    }
  }
  .content {
    position: relative;
    top: 4px;
    flex: 1 1 auto;
    margin-left: 24px;
    color: var(--pro-ant-color-text-tertiary);
    line-height: 22px;
    .contentTitle {
      margin-bottom: 12px;
      color: var(--pro-ant-color-text);
      font-weight: 500;
      font-size: 20px;
      line-height: 28px;
    }
  }
}

.projectList {
  :deep(.ant-card-meta-description) {
    height: 44px;
    overflow: hidden;
    color: var(--pro-ant-color-text-tertiary);
    line-height: 22px;
  }
  .cardTitle {
    font-size: 0;
    a {
      display: inline-block;
      height: 24px;
      margin-left: 12px;
      color: var(--pro-ant-color-text);
      font-size: 14px;
      line-height: 24px;
      vertical-align: top;
      &:hover {
        color: var(--pro-ant-color-primary-hover);
      }
    }
  }
  .projectGrid {
    width: 33.33%;
  }
  .projectItemContent {
    display: flex;
    height: 20px;
    margin-top: 8px;
    overflow: hidden;
    font-size: 12px;
    line-height: 20px;
    .textOverflow();
    a {
      display: inline-block;
      flex: 1 1 0;
      color: var(--pro-ant-color-text-tertiary);
      .textOverflow();
      &:hover {
        color: var(--pro-ant-color-primary-hover);
      }
    }
    .datetime {
      flex: 0 0 auto;
      float: right;
      color: var(--pro-ant-color-text-quaternary);
    }
  }
}

.datetime {
  color: var(--pro-ant-color-text-quaternary);
}

@media screen and (max-width: 1200px) and (min-width: 992px) {
  .activeCard {
    margin-bottom: 24px;
  }
}

@media screen and (max-width: 992px) {
  .activeCard {
    margin-bottom: 24px;
  }
}

@media screen and (max-width: 768px) {
  .projectList {
    .projectGrid {
      width: 50%;
    }
  }
}

@media screen and (max-width: 576px) {
  .pageHeaderContent {
    display: block;
    .content {
      margin-left: 0;
    }
  }
}

@media screen and (max-width: 480px) {
  .projectList {
    .projectGrid {
      width: 100%;
    }
  }
}
</style>
