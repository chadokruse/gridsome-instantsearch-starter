<template>
  <Layout>

    <ClientOnly>
      <div class="container">
        <ais-instant-search
          :search-client="searchClient"
          index-name="instant_search"
        >
          <div class="search-panel">
            <div class="search-panel__filters">
              <ais-refinement-list attribute="brand" />
            </div>

            <div class="search-panel__results">
              <div class="searchbox">
                <ais-search-box placeholder="" />
              </div>
              <ais-hits>
                <template slot="item" slot-scope="{ item }">
                  <article>
                    <h1>
                      <ais-highlight :hit="item" attribute="name" />
                    </h1>
                    <p>
                      <ais-highlight :hit="item" attribute="description" />
                    </p>
                  </article>
                </template>
              </ais-hits>

              <div class="pagination">
                <ais-pagination />
              </div>
            </div>
          </div>
        </ais-instant-search>
      </div>
    </ClientOnly>

  </Layout>
</template>

<script>
// This boilerplate is focsed solely on client-side search
// It assumes data is synced to Algolia outside Gridsome
// If you want data synced at Gridsome build time (e.g. blog posts), see https://gridsome.org/plugins/gridsome-plugin-algolia

// Install Algolia Javascript API client
import algoliasearch from 'algoliasearch/lite';

// Install optional Algolia theme
import 'instantsearch.css/themes/satellite.css';

export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  data() {
    return {
      searchClient: algoliasearch('latency', '6be0576ff61c053d5f9a3225e2a90f76'),
    };
  },
}
</script>

<style>
.search-panel {
  display: flex;
}

.search-panel__filters {
  flex: 1;
}

.search-panel__results {
  flex: 3;
}

.searchbox {
  margin-bottom: 2rem;
}

.ais-Hits {
  margin-bottom: 2rem;
}

.pagination {
  margin: 2rem auto;
  text-align: center;
}

</style>
