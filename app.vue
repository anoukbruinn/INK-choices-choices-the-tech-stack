<template>
  <div>
    <h1>Hello</h1>
  </div>
</template>

const runtimeConfig = useRuntimeConfig();
const { data, error } = await useFetch('https://graphql.datocms.com', {
    method: 'POST',
    headers: {
        Authorization: `Bearer ${runtimeConfig.public.datoCmsToken}`,
    },
    body: {
        query: QUERY,
    },
    transform: ({ data, errors }) => {
        if (errors) throw new errors;

        return data;
    },
});
