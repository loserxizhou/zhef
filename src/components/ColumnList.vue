<template>
  <div class="row">
      <div class="col-4 mb-4" v-for="column in columnList" :key="column.id">
          <div class="card h-100 shadow-sm">
            <div class="card-body text-center">
              <img class="rounded-circle border border-right w-25 my-3" :src="column.avatar" :alt="column.title">
              <h5 class="card-title">{{column.title}}</h5>
              <p class="card-text text-left">{{column.description}}</p>
              <a class="btn btn-outline-primary" href="#">进入专栏</a>
            </div>
          </div>
      </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent, PropType, computed } from 'vue'
export interface ColumnPorps {
    id: number;
    title: string;
    avatar?: string;
    description: string;
}
export default defineComponent({
  name: 'ColumnList',
  props: {
    list: {
      type: Array as PropType<ColumnPorps[]>,
      required: true
    }
  },
  setup (props) {
    const columnList = computed(() => {
      return props.list.map((column) => {
        if (!column.avatar) {
          column.avatar = 'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1605846565466&di=b5570bab87657e7aca8fd21684232c54&imgtype=0&src=http%3A%2F%2Fpic.soutu123.com%2Felement_origin_min_pic%2F01%2F40%2F65%2F61573d0bf6a3c2b.jpg%2521%2Ffw%2F700%2Fquality%2F90%2Funsharp%2Ftrue%2Fcompress%2Ftrue'
        }
        return column
      })
    })
    return {
      columnList
    }
  }
})
</script>
