# React + TypeScript + Vite

このテンプレートは、Vite で React を動作させるための最小限のセットアップを提供します。HMR (Hot Module Replacement) といくつかの ESLint ルールが含まれています。

現在、2つの公式プラグインが利用可能です。

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md): 高速リフレッシュのために [Babel](https://babeljs.io/) を使用します。
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc): 高速リフレッシュのために [SWC](https://swc.rs/) を使用します。

## ESLint 設定の拡張

本番アプリケーションを開発している場合は、型認識の lint ルールを有効にするために設定を更新することをお勧めします。

- トップレベルの `parserOptions` プロパティを次のように設定します。

```js
export default tseslint.config({
  languageOptions: {
    // その他のオプション...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- `tseslint.configs.recommended` を `tseslint.configs.recommendedTypeChecked` または `tseslint.configs.strictTypeChecked` に置き換えます。
- オプションで `...tseslint.configs.stylisticTypeChecked` を追加します。
- [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) をインストールし、設定を更新します。

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // React のバージョンを設定
  settings: { react: { version: '18.3' } },
  plugins: {
    // react プラグインを追加
    react,
  },
  rules: {
    // その他のルール...
    // 推奨ルールを有効化
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
