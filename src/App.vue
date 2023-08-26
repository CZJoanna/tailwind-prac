<template>
  <el-dialog v-model="dialogTableVisible" title="新增特殊房價">
    <!-- 適用期間 -->
    <span>適用期間</span>
    <div class="mb-[1rem]">
      <el-date-picker
        v-model="dateRange"
        type="daterange"
        start-placeholder="Start Date"
        end-placeholder="End Date"
        format="YYYY/MM/DD"
        value-format="YYYY-MM-DD"
      />
    </div>
    <!-- 請先填寫房價 -->
    <span>請先填寫房價，再勾選房型</span>
    <!-- 按鈕群 -->
   <div class="mb-[1rem]">
    <el-checkbox-group v-model="list">
      <el-checkbox 
        v-for="roomType in roomTypes" 
        :label="roomType"
        :disabled="!roomType.price"
        border
        size="large"
        class="mb-[1rem]"
        >
        {{ roomType.name }}
        <el-input-number
          v-model="roomType.price"
          :min="1"
          controls-position="right"
          :controls="false"
        />
      </el-checkbox>
    </el-checkbox-group>

   </div>
   <!-- 星期 -->
   <span>此特殊房價可用於星期幾？</span>
   <div>
      <el-checkbox-group
      v-model="checkedWeeks"
    >
      <el-checkbox v-for="(weekName, i) in week" :key="weekName" :label="i">{{
        weekName
      }}</el-checkbox>
    </el-checkbox-group>
   </div>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogTableVisible = false">Cancel</el-button>
        <el-button type="primary" @click="dialogTableVisible = false">
          Confirm
        </el-button>
      </span>
    </template>
  </el-dialog>
  <el-dialog v-model="dialogEditVisible" title="編輯特殊房價">
  <div class="flex flex-col items-start mb-[1rem]">
    <span>日期</span>
    <el-date-picker
      v-model="editInfo.date_range"
      type="daterange"
      start-placeholder="Start Date"
      end-placeholder="End Date"
      format="YYYY/MM/DD"
      value-format="YYYY-MM-DD"
      :clearable="false"
    />
  </div>
  <div class="flex flex-col items-start">
    <span>房價</span>
    <el-input-number
      v-model="editInfo.price"
      :min="1"
      :controls="false"
    />
  </div>

  <div 
    class="flex flex-col items-start mb-[1rem]"
  >
    <span>適用在星期幾?</span>
    <div>
      <el-checkbox-group
        v-model="editInfo.week"
    >
      <el-checkbox v-for="(weekName, i) in week" :key="weekName" :label="i">{{
        weekName
      }}</el-checkbox>
    </el-checkbox-group>
   </div>
  </div>

  </el-dialog>
  <div class="p-[1rem]">
    <div class="flex justify-between">
      <h2>房型價格表</h2>
      <el-button @click="dialogTableVisible = true">
        ＋新增特殊房價
      </el-button>
    </div>
    <div
    class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-[1rem]"
    >
       <RoomCard
        v-for="roomType in roomTypes"
        :key="roomType.id"
        :room-type="roomType"
       >
        <CustomPrice 
          v-for="(priceInfo, i) in roomType.customArr"
          :key="priceInfo"
          :price-info="priceInfo"
          @delete="() => roomType.customArr.splice(i, 1)"
          @edit="openEditDialog(priceInfo)"
        />
       </RoomCard>
    </div>
  
  </div>
</template>
<script setup>
import CustomPrice from './CustomPrice.vue';
import RoomCard from './RoomCard.vue';
const dateRange = ref([])

const roomTypes = ref([
  {
    id: 1,
    name:'豪華雙人房',
    price: null,
    priceArr: [500, 1000, 2000]

  },
  {
    id: 2,
    name: '豪華四人房',
    price: null,
    priceArr: [100, 100, 500],
    customArr: [
      {
        date_range: ['2023-08-23', '2023-08-31'],
        week: ["0", "1", "2"],
        price: 1000
      },
      // {
      //   date_range: ['2023-09-01', '2023-10-01'],
      //   week: ["0", "1", "2"],
      //   price: 500
      // }
    ]
  },
  {
    id: 3,
    name: '溫馨家庭房',
    price: null,
    priceArr: [null, null, 300]
  
  },
  {
    id: 4,
    name: '海景雙床房',
    price: null,
    priceArr: [100, 300, 500]
  }
]);


const dialogTableVisible = ref(false);
const dialogEditVisible = ref(false)

const list = ref([]);

const week = {
  0: '週日',
  1: '週一',
  2: '週二',
  3: '週三',
  4: '週四',
  5: '週五',
  6: '週六',
};
const checkedWeeks = ref(Object.keys(week))

const editInfo = ref({})
const openEditDialog = (info) => {
  editInfo.value = {...info};
  dialogEditVisible.value = true;

}
</script>

<style scoped>
::v-deep() {
  .el-input-number {
    width: auto;
  }
}
</style>