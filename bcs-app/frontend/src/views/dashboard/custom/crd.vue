<template>
    <BaseLayout title="CRD" kind="CustomResourceDefinition" type="crd" default-active-detail-type="yaml" :show-name-space="false" :show-create="false" :show-detail-tab="false">
        <template #default="{ curPageData, pageConf, handlePageChange, handlePageSizeChange, handleGetExtData, handleSortChange, handleShowDetail }">
            <bk-table
                :data="curPageData"
                :pagination="pageConf"
                @page-change="handlePageChange"
                @page-limit-change="handlePageSizeChange"
                @sort-change="handleSortChange">
                <bk-table-column :label="$t('名称')" prop="metadata.name" sortable>
                    <template #default="{ row }">
                        <bk-button class="bcs-button-ellipsis" text @click="handleShowDetail(row)">{{ row.metadata.name }}</bk-button>
                    </template>
                </bk-table-column>
                <bk-table-column label="Scope" :resizable="false">
                    <template #default="{ row }">
                        <span>{{ handleGetExtData(row.metadata.uid, 'scope') }}</span>
                    </template>
                </bk-table-column>
                <bk-table-column label="Kind" :resizable="false">
                    <template #default="{ row }">
                        <span>{{ handleGetExtData(row.metadata.uid, 'kind') }}</span>
                    </template>
                </bk-table-column>
                <bk-table-column label="ApiVersion" :resizable="false">
                    <template #default="{ row }">
                        <span>{{ handleGetExtData(row.metadata.uid, 'api_version') }}</span>
                    </template>
                </bk-table-column>
                <bk-table-column label="Age" :resizable="false" :show-overflow-tooltip="false">
                    <template #default="{ row }">
                        <span v-bk-tooltips="{ content: handleGetExtData(row.metadata.uid, 'createTime') }">{{ handleGetExtData(row.metadata.uid, 'age') }}</span>
                    </template>
                </bk-table-column>
            </bk-table>
        </template>
    </BaseLayout>
</template>
<script>
    import { defineComponent } from '@vue/composition-api'
    import BaseLayout from '@/views/dashboard/common/base-layout'

    export default defineComponent({
        name: 'CRD',
        components: { BaseLayout }
    })
</script>
