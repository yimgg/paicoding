<template>
  <!-- 专栏详情 -->
  <div>
    <a
      :href="'/column/' + column.columnId + '/1'"
      class="item"
    >
      <div class="poster">
        <img
          :src="column.cover"
          :alt="'「' + column.column + '」封面'"
          class="lazy poster-img"
          style=""
          loading="lazy"
        />
      </div>
      <div class="info">
        <div class="title">
          <span class="new-tag-wrap tag" v-if="column.type === 2" style="color: #f8f8f8">上新</span>
          <span class="text-highlight">
            {{column.column}}
          </span>
        </div>

        <div class="author">
            <a :href="'/user/' + column.author" class="flex">
              <div class="flex justify-around">
                <el-avatar size="small">
                  <img :src="column.authorAvatar"
                       class="lazy avatar hero"
                       loading="lazy"
                  />
                </el-avatar>
                <span class="name ml-2 center-content">
                  {{column.authorName}}
                </span>

                  <span class="self-description center-content">
                  |
                </span>

                  <span class="self-description center-content">
                    {{column.authorProfile != null && column.authorProfile ? column.authorProfile : '这人很懒，还没留下简介~'}}
                </span>
              </div>


            </a>
        </div>
        <div class="other">
          <div class="messages">
            <span class="message">
              <span>
                {{column.state == 2 ? '已完结 ' : '已更新 ' + column.count.articleCount + ' 小节 | '}}
              </span>
              <span>
                {{'共 ' + column.count.totalNums + ' 节 | '}}
              </span>
              <span>
                {{column.count.readCount + ' 人已阅读'}}
              </span>
            </span>
<!--            <span class="sale-tooltip" th:if="${column.type == 2 && new java.util.Date().getTime() < column.freeEndTime }" >-->
<!--              <span th:text="${column.type == 2} ? '限时免费': '免费'"></span>-->
<!--              <span class="count-down-text"-->
<!--                    th:data-free-endTime="${column.freeEndTime}"-->
<!--                    th:data-free-startTime="${column.freeStartTime}"-->
<!--                    th:text="''">-->
<!--                    剩余 1 天 12:50:43.92-->
<!--              </span>-->
<!--            </span>-->
          </div>
        </div>

        <span class="text-highlight desc">
          {{column.introduction}}
        </span>
      </div>
    </a>
  </div>
</template>

<script setup lang="ts">

import type { ColumnVoType } from '@/http/ResponseTypes/ColumnType/ColumnListVoType'

const props = defineProps<{
  column: ColumnVoType
}>()

</script>


<style scoped>
.item {
  display: flex;
  padding: 30px;
  box-sizing: border-box;
  position: relative;
  border-bottom: #e5e5e5 1px solid;
  width: 100%;
  max-width: 800px;
  min-width: 800px;
  min-height: 240px;
  background: white;
  border-radius: 8px;
  margin-bottom: 25px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.poster {
  width: 140px;
  height: 180px;
  flex-shrink: 0;
  position: relative;
}

.poster img {
  width: 100%;
  height: 100%;
  border-radius: 2px;
}

.info {
  position: relative;
  flex-grow: 1;
  overflow: hidden;
  box-sizing: border-box;
  font-size: 20px;
  padding-left: 30px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 180px;
}

.info .messages {
  font-size: 18px;
}

.author .name {
  color: #666;
  font-size: 18px;
}

.title {
  font-size: 28px;
  line-height: 36px;
  margin-bottom: 15px;
}

.info .desc {
  margin-top: 12px;
  font-size: 18px;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  color: #666;
  flex-grow: 1;
}

.other {
  margin-top: 8px;
  display: flex;
  align-items: center;
  color: #8a919f;
}

.author {
  margin-top: 8px;
}

.new-tag-wrap {
  padding: 0 8px;
  height: 24px;
  line-height: 24px;
  color: #fff;
  font-size: 14px;
  border-radius: 2px;
  display: inline-block;
  vertical-align: middle;
  cursor: default;
  margin-right: 4px;
  transform: translateY(-3px);
  background-color: #ED722E;
}

.self-description {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin-left: 6px;
  font-size: 18px;
  color: #666;
}

.text-highlight {
  color: #333;
  font-weight: 500;
}

@media screen and (max-width: 768px) {
  .item {
    padding: 20px;
    margin-bottom: 20px;
    min-height: 200px;
  }

  .poster {
    width: 100px;
    height: 150px;
  }

  .title {
    font-size: 22px;
    line-height: 30px;
  }
  
  .info {
    font-size: 16px;
    padding-left: 20px;
    min-height: 150px;
  }
  
  .info .messages {
    font-size: 14px;
  }
  
  .author .name {
    font-size: 14px;
  }
  
  .info .desc {
    font-size: 14px;
  }
  
  .self-description {
    font-size: 14px;
  }
}
</style>
