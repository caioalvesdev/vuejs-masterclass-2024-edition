<script setup lang="ts">
import type {  TaskWithProjects } from '@/utils/supaQueries';
import { tasksWithProjectsQuery } from '@/utils/supaQueries';
import { columns } from '@/utils/tableColumns/tasksColumns'

usePageStore().pageData.title = 'My Tasks'

const tasks = ref<TaskWithProjects | null>(null)

const getTasks = async () => {
  const { data, error, status } = await tasksWithProjectsQuery

  if(error) useErrorStore().setError({ error, customCode: status })

  tasks.value = data

}

await getTasks()
</script>

<template>
  <DataTable
    v-if="tasks"
    :columns="columns"
    :data="tasks"
  />
</template>
