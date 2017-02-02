---
title: "project.json 参照"
description: "project.json 参照"
keywords: .NET, .NET Core, project.json
author: aL3891
ms.author: mairaw
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3aef32bd-ee2a-4e24-80f8-a2b615e0336d
translationtype: Human Translation
ms.sourcegitcommit: 4023c5ec72055fee78863a43b60989e1eb34fb22
ms.openlocfilehash: 68b152cda54b5356dce48f4a8330b2ecb9c9d2e0

---

# <a name="projectjson-reference"></a>project.json 参照

project.json ファイルは .NET Core プロジェクトで利用され、プロジェクトのメタデータ、コンパイル情報、依存関係を定義します。 この参照トピックでは、project.json ファイルで定義できるすべてのプロパティの一覧を確認できます。

> [!NOTE]
> .NET Core ツールは今後のリリースで project.json から MSBuild ベースのプロジェクトに移行されます。 新しい .NET Core プロジェクトには引き続き project.json ファイルを使用することが推奨されます。ツールがリリースされたとき、プロジェクトを MSBuild に変換するためのパスが与えられるためです。
>
> 詳細については、.NET ブログ投稿の「[Changes to project.json](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)」 (project.json に変更する) と「[Using MSBuild to build .NET Core projects](../tutorials/target-dotnetcore-with-msbuild.md)」 (MSBuild を利用して .NET Core プロジェクトを構築する) トピックを参照してください。

## <a name="overview"></a>概要

```
{
    "name": String,
    "version": String,
    "description": String,
    "copyright": String,
    "title": String,
    "entryPoint": String,
    "testRunner": String,
    "authors": String[],
    "language": String,
    "embedInteropTypes": Boolean,
    "preprocess": String or String[],
    "shared": String or String[],
    "dependencies": Object {
        version: String,
        type: String,
        target: String,
        include: String,
        exclude: String,
        suppressParent: String
    },
    "tools": Object,
    "scripts": Object,
    "buildOptions": Object {
        "define": String[],
        "nowarn": String[],
        "additionalArguments": String[],
        "warningsAsErrors": Boolean,
        "allowUnsafe": Boolean,
        "emitEntryPoint": Boolean,
        "optimize": Boolean,
        "platform": String,
        "languageVersion": String,
        "keyFile": String,
        "delaySign": Boolean,
        "publicSign": Boolean,
        "debugType": String,
        "xmlDoc": Boolean,
        "preserveCompilationContext": Boolean,
        "outputName": String,
        "compilerName": String,
        "compile": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "embed": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "copyToOutput": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "publishOptions": Object {
        "include": String or String[],
        "exclude": String or String[],
        "includeFiles": String or String[],
        "excludeFiles": String or String[],
        "builtIns": Object,
        "mappings": Object
    },
    "runtimeOptions": Object {
        "configProperties": Object {
            "System.GC.Server": Boolean,
            "System.GC.Concurrent": Boolean,
            "System.GC.RetainVM": Boolean,
            "System.Threading.ThreadPool.MinThreads": Integer,
            "System.Threading.ThreadPool.MaxThreads": Integer
        },
        "framework": Object {
            "name": String,
            "version": String,
        },
        "applyPatches": Boolean
    },
    "packOptions": Object {
        "summary": String,
        "tags": String[],
        "owners": String[],
        "releaseNotes": String,
        "iconUrl": String,
        "projectUrl": String,
        "licenseUrl": String,
        "requireLicenseAcceptance": Boolean,
        "repository": Object {
            "type": String,
            "url": String
        },
        "files": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "analyzerOptions": Object {
        "languageId": String
    },
    "configurations": Object,
    "frameworks": Object {
        "dependencies": Object {
            version: String,
            type: String,
            target: String,
            include: String,
            exclude: String,
            suppressParent: String
        },        
        "frameworkAssemblies": Object,
        "wrappedProject": String,
        "bin": Object {
            assembly: String
        }
    },
    "runtimes": Object,
    "userSecretsId": String
}
```

## <a name="name"></a>name
型: String

プロジェクトの名前。パッケージの名前として使用され、アセンブリ名として使用されます。 このプロパティが指定されない場合、最上位フォルダー名が使用されます。

例:

```json
{
    "name": "MyLibrary"
}
```

## <a name="version"></a>version
型: String

プロジェクトの [Semver](http://semver.org/spec/v1.0.0.html) バージョン。NuGet パッケージにも使用されます。

例:

```json
{
    "version": "1.0.0-*"
}
```

## <a name="description"></a>説明
型: String

プロジェクトの詳しい説明。 アセンブリ プロパティで使用されます。

例:

```json
{
    "description": "This is my library and it's really great!"
}
```

## <a name="copyright"></a>著作権
型: String

プロジェクトの著作権情報。 アセンブリ プロパティで使用されます。

例:

```json
{
    "copyright": "Fabrikam 2016"
}
```

## <a name="title"></a>タイトル
型: String

プロジェクトのわかりやすい名前。スペースを含めることができます。`name` プロパティの使用時、特殊文字は許可されません。 アセンブリ プロパティで使用されます。

例:

```json
{
    "title": "My Library"
}
```

## <a name="entrypoint"></a>entryPoint
型: String

プロジェクトの EntryPoint メソッド。 既定では `Main` です。

次に例を示します。

```json
{
    "entryPoint": "ADifferentMethod"
}
```
    
## <a name="testrunner"></a>testRunner
型: String

テスト ランナーの名前。[NUnit](http://nunit.org/) や [xUnit](http://xunit.github.io/) など。このプロジェクトで使用されます。 これを設定すると、プロジェクトがテスト プロジェクトとしても設定されます。

例:

```json
{
    "testRunner": "NUnit"
}
```

## <a name="authors"></a>作成者
型: String[]

プロジェクトの作成者の名前を含む文字列の配列。

例:

```json
{
    "authors": ["Anne", "Bob"]
}
```

## <a name="language"></a>language
型: String

プロジェクトの言語 (人間語)。 "ニュートラル言語" コンパイラ引数に対応します。

例:

```json
{
    "language": "en-US"
}
```

## <a name="embedinteroptypes"></a>embedInteropTypes
型: Boolean

アセンブリに COM 相互運用型を埋め込む場合は `true`。そうでない場合は `false`。 

次に例を示します。

```json
{
    "embedInteropTypes": true
}
```

## <a name="preprocess"></a>preprocess
型: String または String[] とグロビング パターン

プリプロセスに含まれるファイルを指定します。

例:

```json
{
    "preprocess": "compiler/preprocess/**/*.cs"
}
```

## <a name="shared"></a>shared
型: String または String[] とグロビング パターン

共有されるファイルを指定します。これがライブラリ エクスポートに使用されます。

例:

```json
{
    "shared": "shared/**/*.cs"
}
```

## <a name="dependencies"></a>依存関係
型: Object

プロジェクトのパッケージ依存関係を定義するオブジェクト。このオブジェクトの各キーがパッケージの名前であり、各値にバージョン情報が含まれています。
詳細については、NuGet ドキュメント サイトの記事「[依存解決](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#dependency-resolution-in-nuget-3-x)」を参照してください。

例:

```json
    "dependencies": {
        "System.Reflection.Metadata": "1.3.0",
        "Microsoft.Extensions.JsonParser.Sources": {
          "type": "build",
          "version": "1.0.0-rc2-20221"
        },
        "Microsoft.Extensions.HashCodeCombiner.Sources": {
          "type": "build",
          "version": "1.1.0-alpha1-21456"
        },
        "Microsoft.Extensions.DependencyModel": "1.0.0-*"
    }
```

### <a name="version"></a>version
型: String

依存関係のバージョンまたはバージョン範囲を指定します。 \* ワイルドカードを利用し、[浮動依存関係バージョン](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#floating-versions)を指定します。

例:

```json
"dependencies": { 
    "Newtonsoft.Json": { 
        "version": "9.0.1" 
    }
}
```

### <a name="type"></a>型
型: String

依存関係の型を指定します。 `default`、`build`、`platform` のいずれかの値になります。 既定値は `default` です。

`build` は開発依存関係として知られ、ビルド時にのみ使用されます。 つまり、出力 `.nupkg` ファイルの依存関係としてパッケージを公開したり、追加したりするべきではありません。 [supressParent](#supressparent) を `all` に設定した場合と同じ効果があります。

`platform` は共有 SDK を参照します。 詳細については、「[.NET Core Application Deployment](../deploying/index.md)」(.NET Core アプリケーションの展開) トピックの「Deploying a framework-dependent deployment with third-party dependencies」(サードパーティの依存関係を含む、フレームワークに依存する展開を展開する) セクションを参照してください。

次に例を示します。

```json
 "dependencies": {
   "Microsoft.NETCore.App": {
     "type": "platform",
     "version": "1.0.0"
   }
 }
```

### <a name="target"></a>target
型: String

`project` または `package` にのみ一致するように依存関係を制約します。

### <a name="include"></a>include
型: String

依存関係パッケージの一部を含みます。 `all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers`、`none` というフラグの 1 つまたは複数を指定できます。
複数のフラグはコンマ区切りリストで定義されます。
詳細については、NuGet リポジトリの「[Managing dependency package assets](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)」 (依存関係パッケージ資産の管理) 仕様を参照してください。

例:

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "include": "runtime"
    }
  }
}
```

### <a name="exclude"></a>exclude
型: String

依存関係パッケージの一部を除外します。 `all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers`、`none` というフラグの 1 つまたは複数を指定できます。
複数のフラグはコンマ区切りリストで定義されます。
詳細については、NuGet リポジトリの「[Managing dependency package assets](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)」 (依存関係パッケージ資産の管理) 仕様を参照してください。

例:

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "exclude": "contentFiles"
    }
  }
}
```

### <a name="supressparent"></a>supressParent
型: String

プロジェクトのコンシューマーの追加除外を定義します。 `all`、`runtime`、`compile`、`build`、`contentFiles`、`native`、`analyzers`、`none` というフラグの 1 つを指定できます。
詳細については、NuGet リポジトリの「[Managing dependency package assets](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets)」 (依存関係パッケージ資産の管理) 仕様を参照してください。

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "suppressParent": "compile"
    }
  }
}
```

## <a name="tools"></a>ツール
型: Object

参照としてではなく、現行プロジェクトのツールとして使用されるパッケージ依存関係を定義するオブジェクト。 ここに定義されるパッケージはビルド プロセス中に実行されるスクリプトで利用できますが、プロジェクト自体のコードにはアクセスできません。 ツールにはたとえば、パッキング関連のタスクを実行するコード ジェネレーターやビルド後ツールを含めることができます。

例:

```json
{
    "tools": {
    "MyObfuscator": "1.2.4"
    }
}
```

## <a name="scripts"></a>スクリプト
型: Object

ビルド プロセス中に実行されるスクリプトを定義するオブジェクト。 このオブジェクトの各キーにより、スクリプトが実行されるビルド内の箇所が特定されます。 各値は、実行するスクリプトを含む文字列か順番に実行されるスクリプトを含む文字列の配列になります。
サポートされているイベント:
* precompile
* postcompile
* prepublish
* postpublish

例:

```json
{
    "scripts": {
        "precompile": "generateCode.cmd",
        "postcompile": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
    }
}
```

## <a name="buildoptions"></a>buildOptions
型: Object

プロパティがコンパイルのさまざまな側面を制御するオブジェクト。 有効なプロパティの一覧が下にあります。 「[フレームワーク セクション](#frameworks)」の説明のように、ターゲット フレームワークごとに指定することもできます。

例:

```json
    "buildOptions": {
      "allowUnsafe": true,
      "emitEntryPoint": true
    }
```

### <a name="define"></a>define
型: String[]

"DEBUG" や "TRACE" など、コードの条件付きコンパイルで利用できる define の一覧。

例:

```json
{
    "buildOptions": {
        "define": ["TEST", "OTHERCONDITION"]
    }
}
```

### <a name="nowarn"></a>nowarn
型: String[]

無視する警告の一覧。

例:

```json
{
    "buildOptions": {
        "nowarn": ["CS0168", "CS0219"]
    }
}
```

この場合、警告 `The variable 'var' is declared but never used` と `The variable 'var' is assigned but its value is never used` が無視されます。

### <a name="additionalarguments"></a>additionalArguments
型: String[]

コンパイラに渡される追加引数の一覧。

例:

```json
{
    "buildOptions": {
        "additionalArguments": ["/parallel", "/nostdlib"]
    }
}
```

### <a name="warningsaserrors"></a>warningsAsErrors
型: Boolean

すべての警告をエラーとして扱う場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "warningsAsErrors": true
    }
}
```

### <a name="allowunsafe"></a>allowUnsafe
型: Boolean

プロパティでアンセーフ コードを許可する場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "allowUnsafe": true
    }
}
```

### <a name="emitentrypoint"></a>emitEntryPoint
型: Boolean

実行可能ファイルを作成する場合は `true`、ライブラリを生成する場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "emitEntryPoint": true
    }
}
```

### <a name="optimize"></a>optimize
型: Boolean

このプロジェクトでコンパイラがコードを最適化できるようにする場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "optimize": true
    }
}
```

### <a name="platform"></a>platform
型: String

AnyCpu、x86、x64 など、ターゲット プラットフォームの名前。

例:

```json
{
    "buildOptions": {
        "platform": "x64"
    }
}
```

### <a name="languageversion"></a>languageVersion
型: String

コンパイラで使用される言語のバージョン: ISO-1、ISO-2、3、4、5、6、既定値。

例:

```json
{
    "buildOptions": {
        "languageVersion": "5"
    }
}
```

### <a name="keyfile"></a>keyFile
型: String

このアセンブリの署名に使用されるキー ファイルのパス。

例:

```json
{
    "buildOptions": {
        "keyFile": "../keyfile.snk"
    }
}
```

### <a name="delaysign"></a>delaySign
型: Boolean

署名を遅らせる場合は `true`それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "delaySign": true
    }
}
```

### <a name="publicsign"></a>publicSign
型: Boolean

結果として生成されるアセンブリの署名を有効にする場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "publicSign": true
    }
}
```

### <a name="debugtype"></a>debugType
型: String

生成するシンボル ファイル (PDB ファイル) の種類を示します。 オプションは "portable" (.NET Core プロジェクト) または "full" (従来の Windows 専用 PDB ファイル) です。

例:

```json
{
    "buildOptions": {
        "debugType": "portable"
    }
}
```

### <a name="xmldoc"></a>xmlDoc
型: Boolean

ソース コードにあるスラッシュが 3 つのコメントから XML ドキュメントを生成する場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "xmlDoc": true
    }
}
```

### <a name="preservecompilationcontext"></a>preserveCompilationContext
型: Boolean

参照アセンブリやその他のコンテキスト データを保存し、ランタイム コンパイルを可能にする場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "buildOptions": {
        "preserveCompilationContext": true
    }
}
```

### <a name="outputname"></a>outputName
型: String

出力ファイルの名前を変更します。 

例:

```json
{
    "buildOptions": {
        "outputName": "MyApp"
    }
}
```

### <a name="compilername"></a>compilerName
型: String

このプロジェクトで使用されるコンパイラの名前。 既定では `csc` です。 現在のところ、 `csc` (C# コンパイラ) または `fsc` (F# コンパイラ) がサポートされています。
 
例:

```json
{
    "compilerName": "fsc"
}
```
    
### <a name="compile"></a>compile
型: Object

コンパイル構成のプロパティを含むオブジェクト。

#### <a name="include"></a>include
型: String または String[] とグロビング パターン

ビルドに含めるファイルを指定します。 パターンはプロジェクト フォルダーで root 化されます。 既定値は none (なし) です。

例:

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
型: String または String[] とグロビング パターン

ビルドから除外するファイルを指定します。 「除外する」パターンには「含める」パターンより高い優先度が与えられます。そのため、両方に含まれるファイルは除外されます。 パターンはプロジェクト フォルダーで root 化されます。 既定値は none (なし) です。

例:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

型: String または String[] とグロビング パターン

含めるファイル パスの一覧。 パスはプロジェクト フォルダーで root 化されます。 この一覧には、グロビング パターンの「除外する」または「含める」より高い優先度が与えられます。そのため、この一覧にあり、「除外する」グロビング パターンに入っているファイルは含まれます。 既定値は none (なし) です。

例:

```json
{
    "includeFiles": []
}
```

#### <a name="excludefiles"></a>excludeFiles

型: String または String[] とグロビング パターン

除外するファイル パスの一覧。 パスはプロジェクト フォルダーで root 化されます。 この一覧にはグロビング パターンと「含める」パスより高い優先度が与えられます。そのため、すべてに入っているファイルは除外されます。 既定値は none (なし) です。

例:

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns

型: Object

システムが提供する既定値。 グロビング パターンの `include` と `exclude` を与えることができます。これらは `include` プロパティと `exclude` プロパティの該当値と結合されます。

例:

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>マップ
型: Object

オブジェクトのキーは、出力レイアウトの宛先パスを表します。

値は、含めるファイルのソース パスを表す文字列またはオブジェクトになります。  オブジェクトで表すときは、独自の `include`、`exclude`、`includeFiles`、`excludeFiles` セクションを与えることができます。

文字列の例:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

オブジェクトの例:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="embed"></a>embed
型: Object

コンパイル構成のプロパティを含むオブジェクト。

#### <a name="include"></a>include
型: String または String[] とグロビング パターン

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
型: String または String[] とグロビング パターン

ビルドから除外するファイルを指定します。

例:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

型: String または String[] とグロビング パターン

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

型: String または String[] とグロビング パターン

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
型: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>マップ
型: Object

オブジェクトのキーは、出力レイアウトの宛先パスを表します。

値は、含めるファイルのソース パスを表す文字列またはオブジェクトになります。  オブジェクトで表すときは、独自の `include`、`exclude`、`includeFiles`、`excludeFiles` セクションを与えることができます。

文字列の例:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

オブジェクトの例:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="copytooutput"></a>copyToOutput
型: Object

コンパイル構成のプロパティを含むオブジェクト。

#### <a name="include"></a>include
型: String または String[] とグロビング パターン

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
型: String または String[] とグロビング パターン

ビルドから除外するファイルを指定します。

例:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

型: String または String[] とグロビング パターン

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

型: String または String[] とグロビング パターン

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
型: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>マップ
型: Object

オブジェクトのキーは、出力レイアウトの宛先パスを表します。

値は、含めるファイルのソース パスを表す文字列またはオブジェクトになります。  オブジェクトで表すときは、独自の `include`、`exclude`、`includeFiles`、`excludeFiles` セクションを与えることができます。

文字列の例:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

オブジェクトの例:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="publishoptions"></a>publishOptions
型: Object

コンパイル構成のプロパティを含むオブジェクト。

### <a name="include"></a>include
型: String または String[] とグロビング パターン

```json
{
    "include":["wwwroot", "Views"]
}
```

### <a name="exclude"></a>exclude
型: String または String[] とグロビング パターン

ビルドから除外するファイルを指定します。

例:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

### <a name="includefiles"></a>includeFiles

型: String または String[] とグロビング パターン

```json
{
    "includeFiles":[],
}
```

### <a name="excludefiles"></a>excludeFiles

型: String または String[] とグロビング パターン

```json
{
    "excludeFiles":[],
}
```

### <a name="builtins"></a>builtIns
型: Object

```json
{
    "builtIns":{}
}
```

### <a name="mappings"></a>マップ
型: Object

オブジェクトのキーは、出力レイアウトの宛先パスを表します。

値は、含めるファイルのソース パスを表す文字列またはオブジェクトになります。  オブジェクトで表すときは、独自の `include`、`exclude`、`includeFiles`、`excludeFiles` セクションを与えることができます。

文字列の例:

```json
{
    "mappings": {
        "dest/file": "./src/file",
        "dest/folder/": "./src/folder/**/*"
    }
}
```

オブジェクトの例:

```json
{
    "mappings": {
        "dest/file":{
            "include":"./src/file"
        },
        "dest/folder/":{
            "include":"./src/folder/**/*"
        }
    }
}
```

## <a name="runtimeoptions"></a>runtimeOptions
型: Object

初期化中にランタイムに与えるパラメーターを指定します。

### <a name="configproperties"></a>configProperties
型: Object

ランタイムとフレームワークを構成する構成プロパティが含まれます。

#### <a name="systemgcserver"></a>System.GC.Server
型: Boolean

サーバーのガベージ コレクションを有効にする場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Server": true
        }
    }
}
```

#### <a name="systemgcconcurrent"></a>System.GC.Concurrent
型: Boolean

同時実行ガベージ コレクションを有効にする場合は `true`、それ以外の場合は `false`。 既定値は、`false` です。

例:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Concurrent": true
        }
    }
}
```

#### <a name="systemgcretainvm"></a>System.GC.RetainVM
型: Boolean

削除するべきセグメントを解放してオペレーティング システム (OS) に戻さず、今後使用するために待機リストに配置する場合は `true`、それ以外の場合は `false`。
既定値は、`false` です。

例:

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.RetainVM": true
        }
    }
}
```

#### <a name="systemthreadingthreadpoolminthreads"></a>System.Threading.ThreadPool.MinThreads
型: Integer

ThreadPool worker プールの最小スレッド数を上書きします。

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MinThreads": 4
        }
    }
}
```

#### <a name="systemthreadingthreadpoolmaxthreads"></a>System.Threading.ThreadPool.MaxThreads
型: Integer

ThreadPool worker プールの最大スレッド数を上書きします。

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MaxThreads": 25
        }
    }
}
```

### <a name="framework"></a>フレームワーク
型: Object

アプリケーションの有効化時に使用する共有フレームワーク プロパティが含まれます。 このセクションが存在することは、アプリケーションが共有の再頒布可能フレームワークを使用するように設計された携帯アプリであることを示します。

#### <a name="name"></a>name
型: String

共有フレームワークの名前。

```json
{
    "runtimeOptions": {
        "framework": {
            "name": "Microsoft.DotNetCore"
        }
    }
}
```

#### <a name="version"></a>version
型: String

共有フレームワークのバージョン。

```json
{
    "runtimeOptions": {
        "framework": {
            "version": "1.0.1"
        }
    }
}
```

### <a name="applypatches"></a>applyPatches
型: Boolean

`true` では、`SemVer` パッチ フィールドでのみ異なる、バージョンが同じかそれより上のフレームワークを使用します。 `false` の場合、ホストで正確なフレームワーク バージョンのみが使用されます。 既定値は、`true` です。

```json
{
    "runtimeOptions": {
        "applyPatches": false
    }
}
```

## <a name="packoptions"></a>packOptions
型: Object

NuGet パッケージに出力されるプロジェクトのパッケージングに関連するオプションを定義します。

### <a name="summary"></a>概要
型: String

プロジェクトの簡単な説明。

例:

```json
{
    "packOptions": {
        "summary": "This is my library."
    }
}
```

### <a name="tags"></a>タグ
型: String[]

NuGet の検索に使用されるプロジェクトのタグを含む文字列の配列。

例:

```json
{
    "packOptions": {
        "tags": ["hyperscale", "cats"]
    }
}
```

### <a name="owners"></a>owners
型: String[]

プロジェクトの所有者の名前を含む文字列の配列。

例:

```json
{
    "packOptions": {
        "owners": ["Fabrikam", "Microsoft"]
    }
}
```

### <a name="releasenotes"></a>releaseNotes
型: String

プロジェクトのリリース ノート。

例:

```json
{
    "packOptions": {
        "releaseNotes": "Initial version, implemented flimflams."
    }
}
```

### <a name="iconurl"></a>iconUrl
型: String

パッケージ エクスプローラーなど、さまざまな場所で使用されるアイコンの URL。

例:

```json
{
    "packOptions": {
        "iconUrl": "http://www.mylibrary.gov/favicon.ico"
    }
}
```

### <a name="projecturl"></a>projectUrl
型: String

プロジェクトのホームページの URL。

例:

```json
{
    "packOptions": {
        "projectUrl": "http://www.mylibrary.gov"
    }
}
```

### <a name="licenseurl"></a>licenseUrl
型: String

プロジェクトで使用されるライセンスの URL。

例:

```json
{
    "packOptions": {
        "licenseUrl": "http://www.mylibrary.gov/licence"
    }
}
```

### <a name="requirelicenseacceptance"></a>requireLicenseAcceptance
型: Boolean

パッケージをインストールしたとき、パッケージの使用許諾に同意を求めるメッセージを表示する場合は `true`、それ以外の場合は `false`。 NuGet パッケージでのみ利用されます。その以外の場合は無視されます。 既定値は、`false` です。

例:

```json
{
    "packOptions": {
        "requireLicenseAcceptance": true
    }
}
```
   
### <a name="repository"></a>リポジトリ
型: Object

プロジェクトが保存されているリポジトリに関する情報が含まれます。

#### <a name="type"></a>型
型: String

リポジトリの種類。 既定値は "git" です。

例:

```json
{
    "packOptions": {
        "repository": {
            "type": "git"
        }
    }
}
```

#### <a name="url"></a>url
型: String

プロジェクトが保存されているリポジトリの URL。

例:

```json
{
    "packOptions": {
        "repository": {
            "url": "http://github.com/dotnet/corefx"
        }
    }
}
```

### <a name="files"></a>ファイル
型: Object

#### <a name="include"></a>include
型: String または String[] とグロビング パターン

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
型: String または String[] とグロビング パターン

ビルドから除外するファイルを指定します。

例:

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

型: String または String[] とグロビング パターン

```json
{
    "includeFiles":[]
}
```

#### <a name="excludefiles"></a>excludeFiles

型: String または String[] とグロビング パターン

```json
{
    "excludeFiles":[]
}
```

#### <a name="builtins"></a>builtIns
型: Object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>マップ
型: Object

オブジェクトのキーは、出力レイアウトの宛先パスを表します。

値は、含めるファイルのソース パスを表す文字列またはオブジェクトになります。  オブジェクトで表すときは、独自の `include`、`exclude`、`includeFiles`、`excludeFiles` セクションを与えることができます。 

文字列の例:

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

オブジェクトの例:

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="analyzeroptions"></a>analyzerOptions
型: Object

コード アナライザーで使用されるプロパティを含むオブジェクト。

例:

```json
{
    "analyzerOptions": { }
}
```

### <a name="languageid"></a>languageId
型: String

解析する言語の ID。 "cs" は C# を表し、"vb" は Visual Basic を表し、"fs" は F# を表します。

例:

```json
"analyzerOptions": {
    "languageId": "vb"
}
```

## <a name="configurations"></a>構成
型: Object

Debug や Release など、プロパティがこのプロジェクトのさまざまな構成を定義するオブジェクト。 各値は、この構成に固有のオプションを含む `buildOptions` オブジェクトを含めることができるオブジェクトです。

例:

```json
"configurations": {
    "Release": {
        "buildOptions": {
            "allowUnsafe": false
        }
    }
}
```

## <a name="frameworks"></a>frameworks
型: Object

.NET Framework や Universal Windows Platform (UWP) など、このプロジェクトでサポートされるフレームワークを指定します。 有効なターゲット フレームワーク モニカー (TFM) にする必要があります。 各値は、後続セクションのプロパティの他に、`buildOptions`、`analyzerOptions`、`dependencies` など、このフレームワークに固有の情報を含めることができるオブジェクトです。

例:

```json
"frameworks": {
    "netcoreapp1.0": {
        "buildOptions": {
            "define": ["FOO", "BIZ"]
        }
    }
}
```

### <a name="dependencies"></a>依存関係
型: Object

このフレームワークに固有の依存関係。 これは、すべてのターゲットをまたいでパッケージ レベルの依存関係を指定できないシナリオで便利です。 あるターゲットでは他のターゲットに与えられているビルトイン サポートがないこと、他のターゲットとは異なるバージョンの依存関係が要求されることなどがその理由です。 このノードの他のプロパティの一覧を確認するには、先の「[依存関係](#dependencies)」セクションを参照してください。

例:

```json
    "frameworks": {
        "netstandard1.5": {
        "dependencies": {
            "Microsoft.Extensions.JsonParser.Sources": "1.0.0-rc2-20221"
        }
    }
}
```

### <a name="frameworkassemblies"></a>frameworkAssemblies
型: Object

依存関係と似ていますが、NuGet パッケージではない GAC のアセンブリの参照が含まれます。 依存関係の種類の他、使用するバージョンも指定できます。 .NET Framework やポータブル クラス ライブラリ (PCL) ターゲットをターゲットにするときに使用されます。 Windows では、これが指定されたプロジェクトのみをビルドできます。

例:

```json
"frameworks": {
    "net451": {
        "frameworkAssemblies": {
            "System.Runtime": {
                "type": "build",
                "version": "4.0.0"
            }
        }
    }
}
```

### <a name="wrappedproject"></a>wrappedProject
型: String

依存関係プロジェクトの場所を指定します。 

例:

```json
"frameworks": {
    "net451": {
        "wrappedProject": "MyProject.csproj"
    }
}
```

### <a name="bin"></a>bin
型: Object

DLL ファイルをラップするために使用されます。 この DLL を含むパッケージを参照し、生成できます。 

値がアセンブリ パスである String プロパティ、`assembly` が 1 つ含まれます。   

例:

```json
"frameworks": {
    "netcoreapp1.0": {
        "bin": {
            "assembly": "c:/otherProject/otherdll.dll"
        }
    }
}
```

## <a name="runtimes"></a>runtimes
型: Object

([自己完結型の展開](../deploying/index.md#self-contained-deployments-scd)で使用される) プロジェクトでサポートされる[ランタイム ID (RID)](../rid-catalog.md) の一覧。

例:

```json
"runtimes": {
    "win7-x64": {},
    "win8-x64": {},
    "win81-x64": {},
    "win10-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
}
```

## <a name="usersecretsid"></a>userSecretsId
型: String

開発時に使用されるユーザー シークレット ID を指定します。 詳細については、「[Safe storage of app secrets during development](https://docs.asp.net/en/latest/security/app-secrets.html)」 (開発中のアプリ シークレットの安全な保存) を参照してください。

例:

```json
{
    "userSecretsId": "aspnet-WebApp1-c23d27a4-eb88-4b18-9b77-2a93f3b15119"
}
```



<!--HONumber=Jan17_HO3-->


