## New version 1.0.0-4

We are working towards releasing 1.0 and releasing betas to reach that goal. Notable changes include React 15 compatibility (completed), Typescript 2.2 updates (completed), Elasticsearch 5 support (in progress).

Please help us test 1.0.0 by using the beta releases. 1.0.0-3 is the latest release.

## What is Searchkit?
Searchkit is a suite of UI components built in react. The aim is to rapidly create beautiful search applications using declarative components, and without being an ElasticSearch expert.

<img src="./docs/assets/codepreview.png"/>

[<img src="https://circleci.com/gh/searchkit/searchkit.png?style=shield"/>](https://circleci.com/gh/searchkit/searchkit)
[![npm version](https://badge.fury.io/js/searchkit.svg)](https://badge.fury.io/js/searchkit)
[![Join the chat at https://gitter.im/searchkit/searchkit](https://badges.gitter.im/searchkit/searchkit.svg)](https://gitter.im/searchkit/searchkit?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Coverage Status](https://coveralls.io/repos/searchkit/searchkit/badge.svg?branch=develop&service=github)](https://coveralls.io/github/searchkit/searchkit?branch=develop)

See full [Documentation](http://docs.searchkit.co/stable) or [Getting Started](http://docs.searchkit.co/stable/docs/setup/project-setup.html)

## Quick Intro
[Live demo](http://demo.searchkit.co)

```jsx
const searchkit = new SearchkitManager("http://demo.searchkit.co/api/movies/")


const App = ()=> (
  <SearchkitProvider searchkit={searchkit}>
    <Layout>
      <TopBar>
        <SearchBox
          autofocus={true}
          searchOnChange={true}
          prefixQueryFields={["actors^1","type^2","languages","title^10"]}/>
      </TopBar>
      <LayoutBody>
        <SideBar>
          <HierarchicalMenuFilter
            fields={["type.raw", "genres.raw"]}
            title="Categories"
            id="categories"/>
          <RefinementListFilter
            id="actors"
            title="Actors"
            field="actors.raw"
            operator="AND"
            size={10}/>
        </SideBar>
        <LayoutResults>
          <ActionBar>

            <ActionBarRow>
              <HitsStats/>
            </ActionBarRow>

            <ActionBarRow>
              <SelectedFilters/>
              <ResetFilters/>
            </ActionBarRow>

          </ActionBar>
          <Hits mod="sk-hits-grid" hitsPerPage={10} itemComponent={MovieHitsGridItem}
            sourceFilter={["title", "poster", "imdbId"]}/>
          <NoHits/>
        </LayoutResults>
      </LayoutBody>
    </Layout>
  </SearchkitProvider>
)

ReactDOM.render(<App/>, document.getElementById('root'))


```
