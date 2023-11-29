<template>
  <div class="home">
    <div class="equipment-box">
      <div class="clumns-header">
        <div class="header-l"></div>
        <div class="columns-item-name" v-for="([key, value], idx) in Object.entries(materialMap)" :key="idx">{{ key }}</div>
      </div>      
      <div class="rows" v-for="([key, value], index) in Object.entries(materialMap)" :key="index">
        <div class="rows-item-name">{{ key }}</div>
        <div class="columns" v-for="([k, val], idx) in Object.entries(value)" :key="idx">
          <div>{{ val }}</div>
        </div>
      </div>
    </div>    
  </div>
</template>

<script lang="ts" setup>
import { onMounted, ref, reactive } from 'vue'

let materialMap = ref({
	"暴风大剑": {
		"暴风大剑": "死亡之刃",
		"反曲之弓": "巨人杀手",
		"无用大棒": "海克斯科技枪刃",
		"女神之泪": "朔极之矛",
		"锁子甲": "夜之锋刃",
		"负极斗篷": "饮血剑",
		"巨人腰带": "斯特拉克的挑战护手",
		"拳套": "无尽之刃",
		"金铲铲": "真实伤害纹章"
	},
	"反曲之弓": {
		"暴风大剑": "巨人杀手",
		"反曲之弓": "红霸符",
		"无用大棒": "鬼索的狂暴之刃",
		"女神之泪": "斯塔缇克电刃",
		"锁子甲": "泰坦的坚决",
		"负极斗篷": "卢安娜的飓风",
		"巨人腰带": "纳什之牙",
		"拳套": "最后的轻语",
		"金铲铲": "8比特纹章"
	},
	"无用大棒": {
		"暴风大剑": "海克斯科技枪刃",
		"反曲之弓": "鬼索的狂暴之刃",
		"无用大棒": "海克斯科技枪刃",
		"女神之泪": "大天使之杖",
		"锁子甲": "冕卫",
		"负极斗篷": "离子火花",
		"巨人腰带": "莫雷诺秘典",
		"拳套": "珠光护手",
		"金铲铲": "K/DA纹章"
	},
	"女神之泪": {
		"暴风大剑": "朔极之矛",
		"反曲之弓": "斯塔缇克电刃",
		"无用大棒": "大天使之杖",
		"女神之泪": "朔极之矛",
		"锁子甲": "圣盾使的誓约",
		"负极斗篷": "适应性头盔",
		"巨人腰带": "救赎",
		"拳套": "正义之手",
		"金铲铲": "EMO纹章"
	},
	"锁子甲": {
		"暴风大剑": "夜之锋刃",
		"反曲之弓": "泰坦的坚决",
		"无用大棒": "冕卫",
		"女神之泪": "圣盾使的誓约",
		"锁子甲": "泰坦的坚决",
		"负极斗篷": "石像鬼石板甲",
		"巨人腰带": "日炎斗篷",
		"拳套": "坚定之心",
		"金铲铲": "五杀摇滚纹章"
	},
	"负极斗篷": {
		"暴风大剑": "饮血剑",
		"反曲之弓": "卢安娜的飓风",
		"无用大棒": "离子火花",
		"女神之泪": "适应性头盔",
		"锁子甲": "石像鬼石板甲",
		"负极斗篷": "饮血剑",
		"巨人腰带": "薄暮法袍",
		"拳套": "水银",
		"金铲铲": "爵士的纹章"
	},
	"巨人腰带": {
		"暴风大剑": "斯特拉克的挑战护手",
		"反曲之弓": "纳什之牙",
		"无用大棒": "莫雷诺秘典",
		"女神之泪": "救赎",
		"锁子甲": "日炎斗篷",
		"负极斗篷": "薄暮法袍",
		"巨人腰带": "纳什之牙",
		"拳套": "破防者",
		"金铲铲": "心之钢纹章"
	},
	"拳套": {
		"暴风大剑": "无尽之刃",
		"反曲之弓": "最后的轻语",
		"无用大棒": "珠光护手",
		"女神之泪": "正义之手",
		"锁子甲": "坚定之心",
		"负极斗篷": "水银",
		"巨人腰带": "破防者",
		"拳套": "无尽之刃",
		"金铲铲": "朋克纹章"
	},
	"金铲铲": {
		"暴风大剑": "真实伤害纹章",
		"反曲之弓": "8比特纹章",
		"无用大棒": "K/DA纹章",
		"女神之泪": "EMO纹章",
		"锁子甲": "五杀摇滚纹章",
		"负极斗篷": "爵士的纹章",
		"巨人腰带": "心之钢纹章",
		"拳套": "朋克纹章",
		"金铲铲": "金铲铲冠冕"
	}
} as any)

// let materialList = ref([
//   {
//     name: '暴风大剑'
//   },
//   {
//     name: '反曲之弓'
//   },
//   {
//     name: '无用大棒'
//   },
//   {
//     name: '女神之泪'
//   },
//   {
//     name: '锁子甲'
//   },
//   {
//     name: '负极斗篷'
//   },
//   {
//     name: '巨人腰带'
//   },  
//   {
//     name: '拳套'
//   },
//   {
//     name: '金铲铲'
//   },
// ] as any)

// let equipmentList = ref([
//   {
//     name: '死亡之刃',
//     materials: ['暴风大剑', '暴风大剑']
//   },
//   {
//     name: '巨人杀手',
//     materials: ['暴风大剑', '反曲之弓']
//   },
//   {
//     name: '海克斯科技枪刃',
//     materials: ['暴风大剑', '无用大棒']
//   },
//   {
//     name: '朔极之矛',
//     materials: ['暴风大剑', '女神之泪']
//   },
//   {
//     name: '饮血剑',
//     materials: ['暴风大剑', '负极斗篷']
//   },
//   {
//     name: '无尽之刃',
//     materials: ['暴风大剑', '拳套']
//   },
//   {
//     name: '鬼索的狂暴之刃',
//     materials: ['反曲之弓', '无用大棒']
//   },
//   {
//     name: '斯塔缇克电刃',
//     materials: ['反曲之弓', '女神之泪']
//   },
//   {
//     name: '泰坦的坚决',
//     materials: ['反曲之弓', '锁子甲']
//   },
//   {
//     name: '卢安娜的飓风',
//     materials: ['反曲之弓', '负极斗篷']
//   },
//   {
//     name: '纳什之牙',
//     materials: ['反曲之弓', '巨人腰带']
//   },
//   {
//     name: '最后的轻语',
//     materials: ['反曲之弓', '拳套']
//   },
//   {
//     name: '灭世者的死亡之帽',
//     materials: ['无用大棒', '无用大棒']
//   },
//   {
//     name: '大天使之杖',
//     materials: ['无用大棒', '女神之泪']
//   },
//   {
//     name: '离子火花',
//     materials: ['无用大棒', '负极斗篷']
//   },
//   {
//     name: '莫雷诺秘典',
//     materials: ['无用大棒', '巨人腰带']
//   },
//   {
//     name: '珠光护手',
//     materials: ['无用大棒', '拳套']
//   },
//   {
//     name: '蓝霸符',
//     materials: ['女神之泪', '女神之泪']
//   },
//   {
//     name: '救赎',
//     materials: ['女神之泪', '巨人腰带']
//   },
//   {
//     name: '正义之手',
//     materials: ['女神之泪', '拳套']
//   },
//   {
//     name: '棘刺背心',
//     materials: ['锁子甲', '锁子甲']
//   },
//   {
//     name: '日炎斗篷',
//     materials: ['锁子甲', '巨人腰带']
//   },
//   {
//     name: '巨龙之爪',
//     materials: ['负极斗篷', '负极斗篷']
//   },
//   {
//     name: '水银',
//     materials: ['负极斗篷', '拳套']
//   },
//   {
//     name: '狂徒铠甲',
//     materials: ['巨人腰带', '巨人腰带']
//   },
//   {
//     name: '金铲铲冠冕',
//     materials: ['金铲铲', '金铲铲']
//   },
//   {
//     name: '窃贼手套',
//     materials: ['拳套', '拳套']
//   },
//   {
//     name: '破防者',
//     materials: ['拳套', '巨人腰带']
//   },
//   {
//     name: '斯特拉克的挑战护手',
//     materials: ['暴风大剑', '巨人腰带']
//   },
//   {
//     name: '冕卫',
//     materials: ['无用大棒', '锁子甲']
//   },
//   {
//     name: '适应性头盔',
//     materials: ['女神之泪', '负极斗篷']
//   },
//   {
//     name: '薄暮法袍',
//     materials: ['负极斗篷', '巨人腰带']
//   },
//   {
//     name: '红霸符',
//     materials: ['反曲之弓', '反曲之弓']
//   },
//   {
//     name: '坚定之心',
//     materials: ['锁子甲', '拳套']
//   },
//   {
//     name: '夜之锋刃',
//     materials: ['暴风大剑', '锁子甲']
//   },
//   {
//     name: '圣盾使的誓约',
//     materials: ['女神之泪', '锁子甲']
//   },
//   {
//     name: '爵士的纹章',
//     materials: ['金铲铲', '负极斗篷']
//   },
//   {
//     name: 'K/DA纹章',
//     materials: ['金铲铲', '无用大棒']
//   },
//   {
//     name: '五杀摇滚纹章',
//     materials: ['金铲铲', '锁子甲']
//   },
//   {
//     name: '朋克纹章',
//     materials: ['金铲铲', '拳套']
//   },
//   {
//     name: 'EMO纹章',
//     materials: ['金铲铲', '女神之泪']
//   },
//   {
//     name: '心之钢纹章',
//     materials: ['金铲铲', '巨人腰带']
//   },
//   {
//     name: '8比特纹章',
//     materials: ['金铲铲', '反曲之弓']
//   },
//   {
//     name: '真实伤害纹章',
//     materials: ['金铲铲', '暴风大剑']
//   },
//   {
//     name: '石像鬼石板甲',
//     materials: ['锁子甲', '负极斗篷']
//   }
// ] as any)

// const getEquipment = (material1, material2) => {
//   let temp = equipmentList.value.find(equipment => {
//     return (
//       equipment.materials.includes(material1) &&
//       equipment.materials.includes(material2)
//     );
//   })

//   return temp.name
// }

onMounted(() => {
  // let obj = {}
  // for(let i = 0; i < materialList.value.length; i++) {
  //   obj[materialList.value[i].name] = {}
  //   for(let j = 0; j < materialList.value.length; j++) {      
  //     obj[materialList.value[i].name][materialList.value[j].name] = getEquipment(materialList.value[i].name, materialList.value[j].name)
  //   }
  // }

})

</script>

<style lang="less">
.home {
  font-size: 12px;
  .equipment-box {
    width: 1200px;
    .clumns-header {
      display: flex;
      margin-bottom: 10px;
      .header-l {
        width: 150px;
      }
      .columns-item-name {
        width: 200px;
        margin-right: 10px;
      }
    }
    .rows {
      display: flex;
      margin-bottom: 10px;
      .rows-item-name {
        width: 150px;
      }
      .columns {
        width: 200px;
        display: flex;
        margin-right: 10px;
      }
    }
  }  
}
</style>
