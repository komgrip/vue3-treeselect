<template>
    <div>
        <vue-treeselect
            :multiple="true"
            :options="treeData"
            noResultsText="No results..."
            placeholder="Select items..."
            v-model="selected"
            :default-expand-level="0"
            :autoSelectDescendants="false"
            :autoDeselectDescendants="false"
            :searchable="true"
            :show-count="true"
            :always-open="true"
            value-consists-of="LEAF_PRIORITY"
            :disable-branch-nodes="false"
            :search-nested="false"
            :showCountOnSearch="false"
            :allowClearingDisabled="true"
            :allowSelectingDisabledDescendants="true"
        >
            <!-- <template
                #option-label="{ node,
                        shouldShowCount,
                        count,
                        labelClassName,
                        countClassName, }"
            >
                <label :class="labelClassName">
                    {{ node.isBranch ? 'Branch' : 'Leaf' }}: {{ node.label }}
                    <span v-if="shouldShowCount" :class="countClassName">
                        ({{ count }})
                    </span>
                </label>
            </template> -->
        </vue-treeselect>
    </div>
    <div style="margin-top: 500px;">Selected: {{ selected }}</div>
</template>
<script>
import { defineComponent, ref, reactive } from 'vue'

export default defineComponent({
    setup() {
        let selected = ref([])
        let treeOrientation = ref('0')
        let treeData = ref([
            {
                id: 'all',
                label: 'ทั้งหมด',
                children: [
                    {
                        id: 'parent_51',
                        label: 'คู้บอน',
                        children: [
                            {
                                id: '2',
                                label: 'ซอยคู้บอน 35 - ทางคู่ขนานกาญจนาภิเษก',
                            },
                            {
                                id: '3',
                                label:
                                    'ทางคู่ขนานกาญจนาภิเษก - ถนนพระยาสุเรนทร์',
                            },
                            { id: '18', label: 'ถนนรามอินทรา - คลองคู้บอน' },
                        ],
                    },
                    {
                        id: 'parent_54',
                        label: 'ถนนจตุโชติ',
                        children: [
                            {
                                id: '4',
                                label: 'คลองพระยาสุเรนทร์ - ถนนพระยาสุเรนทร์',
                            },
                            {
                                id: '99',
                                label: 'ถนนสุขาภิบาล 5 - คลองหนองควายหาย',
                            },
                            {
                                id: '100',
                                label:
                                    'ถนนคู่ขนานทางพิเศษฉลองรัช - ทางคู่ขนานกาญจนาภิเษก',
                            },
                            {
                                id: '101',
                                label:
                                    'ทางคู่ขนานกาญจนาภิเษก - คลองพระยาสุเรนทร์',
                            },
                            {
                                id: '102',
                                label: 'คลองหนองควายหาย - คลองจ้าหล่า 1',
                            },
                        ],
                    },
                    {
                        id: 'parent_110',
                        label: 'ถนนนิมิตใหม่',
                        children: [
                            {
                                id: '5',
                                label: 'ซอยนิมิตใหม่ 5 - สุดเขตกรุงเทพมหานคร',
                            },
                            {
                                id: '54',
                                label: 'ถนนสุวินทวงศ์ - ซอยนิมิตใหม่ 5',
                            },
                        ],
                    },
                    {
                        id: 'parent_141',
                        label: 'ถนนประชาร่วมใจ',
                        children: [
                            { id: '6', label: 'คลองบึงลำไผ่ - คลองลัดตาเตี้ย' },
                            { id: '55', label: 'ถนนนิมิตใหม่ - คลองบึงไผ่' },
                        ],
                    },
                    {
                        id: 'parent_161',
                        label: 'ถนนพระยาสุเรนทร์',
                        children: [
                            {
                                id: '7',
                                label:
                                    'คลองพระยาสุเรนทร์ 1 (กีบหมู) - สะพานพระยาสุเรนทร์ 2',
                            },
                            { id: '8', label: 'คลองสองตะวันตก - ถนนจตุโชติ' },
                            {
                                id: '9',
                                label:
                                    'สะพานพระยาสุเรนทร์ 2 - ซอยพระยาสุเรนทร์ 6',
                            },
                            {
                                id: '10',
                                label: 'ซอยพระยาสุเรนทร์ 6 - คลองสองตะวันตก',
                            },
                            { id: '56', label: 'ถนนรามอินทรา - คลองลำควายหาย' },
                        ],
                    },
                    {
                        id: 'parent_283',
                        label: 'ถนนสามวา',
                        children: [
                            {
                                id: '11',
                                label: 'ลำรางสามวา - คลองหนึ่งตะวันตก',
                            },
                            { id: '60', label: 'ถนนสุวินทวงศ์ - ลำรางสามวา' },
                        ],
                    },
                    {
                        id: 'parent_323',
                        label: 'ถนนหทัยมิตร',
                        children: [
                            { id: '12', label: 'ถนนนิมิตใหม่ - ถนนหทัยราษฎร์' },
                        ],
                    },
                    {
                        id: 'parent_324',
                        label: 'ถนนหทัยราษฏร์',
                        children: [
                            {
                                id: '13',
                                label: 'ลำรางโต๊ะสุข - คลองสามวาตะวันตก',
                            },
                            {
                                id: '14',
                                label: 'คลองสามวาตะวันตก - สุดเขตกรุงเทพมหานคร',
                            },
                            { id: '63', label: 'ถนนสุวินทวงศ์ - ลำรางโต๊ะสุข' },
                        ],
                    },
                    {
                        id: 'parent_393',
                        label: 'ถนนเลียบคลองสอง',
                        children: [
                            {
                                id: '15',
                                label: 'ถนนพระยาสุเรนทร์ - ถนนหทัยราษฎร์',
                            },
                        ],
                    },
                    {
                        id: 'parent_415',
                        label: 'ถนนไมตรีจิต',
                        children: [
                            {
                                id: '16',
                                label: 'ถนนนิมิตใหม่ - ซอยไมตรีจิต 38',
                            },
                            { id: '17', label: 'ซอยไมตรีจิต 38 - คลองเก้า' },
                            { id: '135', label: 'คลองเก้า - ถนนคลองเก้า' },
                        ],
                    },
                    {
                        id: 'parent_103',
                        label: 'ถนนนวมินทร์',
                        children: [
                            { id: '19', label: 'ถนนรามอินทรา - คลองลำชะล่า' },
                            {
                                id: '45',
                                label:
                                    'คลองชะล่า (ลำรางหลวงวิจิตร) - คลองพังพวย',
                            },
                        ],
                    },
                    {
                        id: 'parent_270',
                        label: 'ถนนสวนสยาม',
                        children: [
                            { id: '20', label: 'ถนนเสรีไทย - ถนนรามอินทรา' },
                        ],
                    },
                    {
                        id: 'parent_400',
                        label: 'ถนนเสรีไทย',
                        children: [
                            { id: '21', label: 'คลองระหัส - ซอยเสรีไทย 42' },
                            { id: '22', label: 'คลองครุ - คลองบางชัน' },
                            { id: '51', label: 'ถนนศรีบูรพา - คลองระหัส' },
                            { id: '64', label: 'คลองบางชัน - สี่แยกมีนบุรี' },
                        ],
                    },
                    {
                        id: 'parent_147',
                        label: 'ถนนประดิษฐ์มนูธรรม',
                        children: [
                            {
                                id: '23',
                                label: 'ถนนรามอินทรา - คลองตาเร่ง (คลองตาเริง)',
                            },
                            {
                                id: '67',
                                label: 'ถนนประเสริมนูกิจ - ถนนสังคมสงเคราะห์',
                            },
                            {
                                id: '68',
                                label:
                                    'คลองตาเร่ง (คลองตาเริง) - ถนนประเสริฐมนูกิจ',
                            },
                            { id: '86', label: 'ถนนลาดพร้าว - คลองลาดพร้าว' },
                            {
                                id: '87',
                                label: 'ถนนสังคมสงเคราะห์ - ถนนลาดพร้าว',
                            },
                        ],
                    },
                    {
                        id: 'parent_153',
                        label: 'ถนนผลาสินธุ์',
                        children: [
                            {
                                id: '24',
                                label: 'ทางลอด ร.11 - ตรงข้ามซอยลาดปลาเค้า 49',
                            },
                            {
                                id: '25',
                                label: 'ตรงข้ามซอยลาดปลาเค้า 49 - คลองหลุมไผ่',
                            },
                            { id: '69', label: 'คลองหลุมไผ่ - ถนนลาดปลาเค้า' },
                        ],
                    },
                    {
                        id: 'parent_174',
                        label: 'ถนนพหลโยธิน',
                        children: [
                            { id: '26', label: 'กม.19+000 - คลองถนน' },
                            {
                                id: '27',
                                label: 'สะพานข้ามคลองบางบัว - กม.18+100',
                            },
                            {
                                id: '104',
                                label: 'คลองถนน - ถนนจันทรุเบกษา (แยก คปอ.)',
                            },
                        ],
                    },
                    {
                        id: 'parent_236',
                        label: 'ถนนลาดปลาเค้า',
                        children: [
                            { id: '28', label: 'คลองหลุมไผ่ - ถนนรามอินทรา' },
                            {
                                id: '70',
                                label: 'สี่แยกวังหิน - ถนนประเสริฐมนูกิจ',
                            },
                            {
                                id: '859',
                                label: 'ถนนประเสริฐมนูกิจ - คลองหลุมไผ่',
                            },
                        ],
                    },
                    {
                        id: 'parent_247',
                        label: 'ถนนวัชรพล',
                        children: [
                            {
                                id: '29',
                                label:
                                    'ทางเข้า ร.ร. อนุบาลโชคชัยชัยพฤกษ์ - คลองจระเข้',
                            },
                            { id: '30', label: 'ถนนเทพรักษ์ - คลองท่าแร้ง' },
                            { id: '31', label: 'คลองจระเข้ - ห้าแยกวัชรพล' },
                            { id: '32', label: 'ห้าแยกวัชรพล - ถนนเทพรักษ์' },
                            {
                                id: '33',
                                label:
                                    'ถนนรามอินทรา - ทางเข้า ร.ร. อนุบาลโชคชัยชัยพฤกษ์',
                            },
                            { id: '105', label: 'คลองท่าแร้ง - ถนนเพิ่มสิน' },
                        ],
                    },
                    {
                        id: 'parent_299',
                        label: 'ถนนสุขาภิบาล 4 (ซ.รามอินทรา 23)',
                        children: [
                            {
                                id: '34',
                                label: 'ถนนรามอินทรา - ซอยรามอินทรา 23 แยก 20',
                            },
                            {
                                id: '35',
                                label:
                                    'ซอยรามอินทรา 23 แยก 20 - ซอยพหลโยธิน 48',
                            },
                        ],
                    },
                    {
                        id: 'parent_300',
                        label: 'ถนนสุขาภิบาล 5',
                        children: [
                            { id: '36', label: 'ถนนเทพรักษ์ - คลองบัวมล' },
                            {
                                id: '37',
                                label: 'ซอยรามอินทรา 39 - ซอยสุขาภิบาล 5 แยก 8',
                            },
                            {
                                id: '38',
                                label: 'ซอยสุขาภิบาล 5 แยก 8 - ถนนเทพรักษ์',
                            },
                            {
                                id: '107',
                                label: 'คลองบัวมล - สุขาภิบาล 5 ซอย 40',
                            },
                            {
                                id: '108',
                                label: 'สุขาภิบาล 5 ซอย 40 - ถนนสายไหม',
                            },
                        ],
                    },
                    {
                        id: 'parent_336',
                        label: 'ถนนอยู่เย็น (รามอินทรา 34)',
                        children: [
                            {
                                id: '39',
                                label:
                                    'สมาคมทหารบกพัฒนา - คลองตาเร่ง (คลองตาเริง)',
                            },
                            {
                                id: '40',
                                label: 'ถนนรามอินทรา - สมาคมทหารบกพัฒนา',
                            },
                        ],
                    },
                    {
                        id: 'parent_373',
                        label: 'ถนนเทพรักษ์',
                        children: [
                            { id: '41', label: 'ถนนพหลโยธิน - คลองลำผักชี' },
                            { id: '42', label: 'ถนนสุขาภิบาล 5 - สุดถนน' },
                            { id: '43', label: 'คลองหนองผักชี - ถนนวัชรพล' },
                            { id: '44', label: 'ถนนวัชรพล - ถนนสุขาภิบาล 5' },
                            { id: '110', label: 'คลองลำผักชี - คลองหนองผักชี' },
                        ],
                    },
                    {
                        id: 'parent_104',
                        label: 'ถนนนวลจันทร์',
                        children: [
                            {
                                id: '46',
                                label:
                                    'ถนนประเสริฐมนูกิจ - ทางหลวงหมายเลข 350(รัชดา_รามอินทรา)',
                            },
                            {
                                id: '47',
                                label:
                                    'ทางหลวงหมายเลข 350(รัชดา_รามอินทรา) - ถนนประดิษฐ์มนูธรรม',
                            },
                        ],
                    },
                    {
                        id: 'parent_228',
                        label: 'ถนนรามอินทรา 40',
                        children: [
                            { id: '48', label: 'ถนนรามอินทรา - ถนนนวลจันทร์' },
                        ],
                    },
                    {
                        id: 'parent_315',
                        label: 'ถนนสุคนธสวัสดิ์',
                        children: [
                            {
                                id: '49',
                                label: 'ถนนนวลจันทร์ - ถนนประดิษฐ์มนูธรรม',
                            },
                            {
                                id: '50',
                                label:
                                    'ถนนประดิษฐ์มนูธรรม - ถนนประดิษฐ์มนูธรรม',
                            },
                            {
                                id: '73',
                                label: 'ถนนประเสริฐมนูกิจ - ถนนประดิษฐ์มนูธรรม',
                            },
                            {
                                id: '74',
                                label:
                                    'ถนนสตรีวิทยา 2 (แยกโรงไม้) - ถนนประเสริฐมนูกิจ',
                            },
                        ],
                    },
                    {
                        id: 'parent_409',
                        label: 'ถนนโพธิ์แก้ว',
                        children: [
                            { id: '52', label: 'ถนนนวมินทร์ - คลองตาหนัง' },
                        ],
                    },
                    {
                        id: 'parent_49',
                        label: 'ถนนคุ้มเกล้า',
                        children: [
                            { id: '53', label: 'ถนนสุวินทวงษ์ - คลองตาเสือ' },
                        ],
                    },
                    {
                        id: 'parent_203',
                        label: 'ถนนมีนพัฒนา',
                        children: [
                            { id: '57', label: 'ถนนเสรีไทย - ถนนรามคำแหง' },
                        ],
                    },
                    {
                        id: 'parent_224',
                        label: 'ถนนรามคำแหง (สุขาภิบาล 3)',
                        children: [
                            { id: '58', label: 'คลองบางชัน - ถนนสุวินทวงศ์' },
                        ],
                    },
                    {
                        id: 'parent_230',
                        label: 'ถนนราษฎร์อุทิศ',
                        children: [
                            {
                                id: '59',
                                label:
                                    'ถนนสุวินทวงศ์ - ถนนเลียบวารี (ลำรางโต๊ะเสาเก่า)',
                            },
                        ],
                    },
                    {
                        id: 'parent_292',
                        label: 'ถนนสีหบุรานุกิจ',
                        children: [
                            { id: '61', label: 'สี่แยกมีนบุรี - คลองสามวา' },
                            { id: '62', label: 'คลองสามวา - ถนนร่มเกล้า' },
                        ],
                    },
                    {
                        id: 'parent_105',
                        label: 'ถนนนาคนิวาส',
                        children: [
                            {
                                id: '65',
                                label: 'ถนนสังคมสงเคราะห์ - คลองสองตอน',
                            },
                            { id: '66', label: 'คลองสองตอน - ถนนสตรีวิทยา 2' },
                        ],
                    },
                    {
                        id: 'parent_240',
                        label: 'ถนนลาดพร้าววังหิน',
                        children: [
                            { id: '71', label: 'ถนนโชคชัย 4 - สี่แยกวังหิน' },
                        ],
                    },
                    {
                        id: 'parent_260',
                        label: 'ถนนสตรีวิทยา 2',
                        children: [
                            {
                                id: '72',
                                label: 'ถนนโชคชัย 4 - ถนนสุคนธสวัสดิ์',
                            },
                        ],
                    },
                    {
                        id: 'parent_335',
                        label: 'ถนนอยู่เย็น',
                        children: [
                            {
                                id: '75',
                                label:
                                    'คลองตาเร่ง (คลองตาเริง) - ถนนประดิษฐ์มนูธรรม',
                            },
                        ],
                    },
                    {
                        id: 'parent_399',
                        label: 'ถนนเสนานิคม 1',
                        children: [
                            {
                                id: '76',
                                label: 'คลองลาดพร้าว - หมู่บ้านเสนานิเวศน์',
                            },
                        ],
                    },
                    {
                        id: 'parent_408',
                        label: 'ถนนโชคชัย 4',
                        children: [
                            {
                                id: '77',
                                label: 'คลองทรงกระเทียม - ถนนโชคชัย 4 แยก 84',
                            },
                            {
                                id: '78',
                                label: 'ถนนโชคชัย 4 แยก 84 - ถนนลาดพร้าววังหิน',
                            },
                            {
                                id: '98',
                                label: 'ถนนลาดพร้าว - คลองทรงกระเทียม',
                            },
                        ],
                    },
                    {
                        id: 'parent_410',
                        label: 'ถนนโยธินพัฒนา',
                        children: [
                            {
                                id: '79',
                                label:
                                    'ถนนประดิษฐ์มนูธรรม(ซ.ประดิษฐฯ23) - ถนนประดิษฐ์มนูธรรม (ซ.ประดิษฐฯ25)',
                            },
                            {
                                id: '80',
                                label:
                                    'ถนนประดิษฐ์มนูธรรม (ซ.ประดิษฐฯ19) - ซอยสหกรณ์ 1 (ซ.ประดิษฐฯ15)',
                            },
                        ],
                    },
                    {
                        id: 'parent_1',
                        label: '(ซ.ลาดพร้าว 64 แยก 4)',
                        children: [
                            {
                                id: '81',
                                label: 'คลองลาดพร้าว - ซอยตะวันรุ่ง 14',
                            },
                        ],
                    },
                    {
                        id: 'parent_8',
                        label: 'ซอยลาดพร้าว 71',
                        children: [
                            {
                                id: '82',
                                label: 'ถนนลาดพร้าว - ถนนสังคมสงเคราะห์',
                            },
                        ],
                    },
                    {
                        id: 'parent_66',
                        label: 'ถนนจันทิมา',
                        children: [
                            {
                                id: '83',
                                label: 'ซอยลาดพร้าว 80 - คลองลาดพร้าว',
                            },
                        ],
                    },
                    {
                        id: 'parent_145',
                        label: 'ถนนประชาอุทิศ',
                        children: [
                            {
                                id: '84',
                                label: 'คลองลาดพร้าว - ถนนประดิษฐ์มนูธรรม',
                            },
                            {
                                id: '85',
                                label: 'ถนนประดิษฐ์มนูธรรม - ถนนศรีวรา',
                            },
                        ],
                    },
                    {
                        id: 'parent_190',
                        label: 'ถนนมหาดไทย (ซ.ลาดพร้าว122/ซ.รามฯ65)',
                        children: [
                            { id: '88', label: 'ถนนลาดพร้าว - คลองแสนแสบ' },
                        ],
                    },
                    {
                        id: 'parent_225',
                        label: 'ถนนรามคำแหง 39',
                        children: [
                            { id: '89', label: 'ถนนศรีวรา - คลองแสนแสบ' },
                        ],
                    },
                    {
                        id: 'parent_237',
                        label: 'ถนนลาดพร้าว',
                        children: [
                            { id: '90', label: 'คลองลาดพร้าว - คลองจั่น' },
                        ],
                    },
                    {
                        id: 'parent_239',
                        label: 'ถนนลาดพร้าว 80',
                        children: [{ id: '91', label: 'ถนนลาดพร้าว - สุดถนน' }],
                    },
                    {
                        id: 'parent_275',
                        label: 'ถนนสังคมสงเคราะห์',
                        children: [
                            {
                                id: '92',
                                label:
                                    'ซอยสังคมสงเคราะห์ 13 - ซอยสังคมสงเคราะห์ 27',
                            },
                            {
                                id: '93',
                                label: 'ถนนนาคนิวาส - ซอยสังคมสงเคราะห์ 13',
                            },
                            { id: '94', label: 'ซอยลาดพร้าว 71 - ถนนนาคนิวาส' },
                            {
                                id: '95',
                                label: 'ถนนประดิษฐ์มนูธรรม - ซอยลาดพร้าว 71',
                            },
                            {
                                id: '96',
                                label: 'ซอยสังคมสงเคราะห์ 27 - ถนนโชคชัย 4',
                            },
                        ],
                    },
                    {
                        id: 'parent_318',
                        label: 'ถนนสุทธิสารวินิจฉัย',
                        children: [
                            {
                                id: '97',
                                label: 'ซอยตะวันรุ่ง 14 - ซอยลาดพร้าว 64',
                            },
                        ],
                    },
                    {
                        id: 'parent_65',
                        label: 'ถนนจันทรุเบกษา',
                        children: [
                            {
                                id: '103',
                                label: 'ถนนพหลโยธิน - ถนนเลียบคลองสอง',
                            },
                        ],
                    },
                    {
                        id: 'parent_285',
                        label: 'ถนนสายไหม',
                        children: [
                            {
                                id: '106',
                                label: 'คลองสอง (คลองถนน) - คลองพระยาสุเรนทร์',
                            },
                        ],
                    },
                    {
                        id: 'parent_360',
                        label: 'ถนนเฉลิมพงษ์',
                        children: [
                            { id: '109', label: 'ถนนสายไหม - คลองหกวา' },
                        ],
                    },
                    {
                        id: 'parent_44',
                        label: 'ถนนคลองสิบ-คลองสิบสี่',
                        children: [
                            {
                                id: '111',
                                label:
                                    'ถนนประชาสำราญ - ถนนเลียบคลองสิบสามฝั่งตะวันตก',
                            },
                            {
                                id: '112',
                                label:
                                    'ถนนเลียบคลองสิบสามฝั่งตะวันตก - ถนนเลียบคลองสิบสี่ฝั่งตะวันตก',
                            },
                            {
                                id: '113',
                                label: 'ถนนคู้-คลองสิบ - ถนนประชาสำราญ',
                            },
                        ],
                    },
                    {
                        id: 'parent_46',
                        label: 'ถนนคลองเก้า',
                        children: [
                            {
                                id: '114',
                                label: 'ถนนไมตรีจิต - สุดเขตกรุงเทพมหานคร',
                            },
                            {
                                id: '115',
                                label: 'ถนนคู้-คลองสิบ - ถนนไมตรีจิต',
                            },
                        ],
                    },
                    {
                        id: 'parent_50',
                        label: 'ถนนคู้-คลองสิบ',
                        children: [
                            {
                                id: '116',
                                label: 'ถนนมิตรไมตรี - สุดเขตกรุงเทพมหานคร',
                            },
                        ],
                    },
                    {
                        id: 'parent_69',
                        label: 'ถนนฉลองกรุง',
                        children: [
                            { id: '117', label: 'คลองลำมะขาม - ถนนสุวินทวงศ์' },
                        ],
                    },
                    {
                        id: 'parent_132',
                        label: 'ถนนบุรีภิรมย์',
                        children: [
                            {
                                id: '118',
                                label: 'ซอยบุรีภิรมย์ 5 - ถนนสังฆสันติสุข',
                            },
                            {
                                id: '119',
                                label: 'คลองลำปลาทิว - ซอยบุรีภิรมย์ 5',
                            },
                        ],
                    },
                ],
            },
        ])

        return {
            treeData,
            selected,
        }
    },
})
</script>
