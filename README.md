# react-test-cicd
=======
# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).


## Memo

- gitlab ci/cdとかgithub actionsでreact appのテスト自動化のテストサンプル

- github/gitlab両方知識がないけど、master/main、developブランチへのpushがあると動作するようになってる

- deployは個人サイトとかappとか考えてないのでつけてない

## 使い方・確認の仕方

まずはこのrepoをcloneする

そしてdevelopブランチに切り替える

`git checkout -b develop`

パッケージインストールしてビルドする

`npm install; npm run build`

とりあえずそのまま動かしてみよう

`npm start`

`localhost:3000`でReactの画面が出ればOK

次にテストを実行してみる

`npm test`

当然成功する

ではここで、testの内容を一部修正してみよう

``` App.test.tsx
test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/hello react/i);
  expect(linkElement).toBeInTheDocument();
});
```
当然失敗するので、この状態でgithubにぷっしゅ！！！

workflowが実行されて、テストの部分で見事にコケるのである！！！

ブランチ保護設定してればCIのテストでこければブランチが改変されない便利！！！

githubのprivate branchではブランチ保護が有効にできないことに注意

ブランチ保護設定で`develop, main`には直接変更ができなくなった！

一度`feature/test`みたいなブランチを切って、`develop`にマージしてみる

ブランチ保護設定がガチガチすぎるとつむ
