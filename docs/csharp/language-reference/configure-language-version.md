---
title: C# 言語のバージョンの選択 - C# ガイド
description: 特定のコンパイラ バージョンを使用して構文の検証を実行するコンパイラを構成します。
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207983"
---
# <a name="select-the-c-language-version"></a>C# 言語のバージョンの選択

C# コンパイラは、既定でリリースされている言語の最新のメジャー バージョンに設定されます。 言語の新しいポイント リリースを使用して、プロジェクトをコンパイルすることができます。 言語の新しいバージョンを選択すると、プロジェクトで最新の言語機能を使用できます。 他のシナリオでは、古いバージョンの言語を使用する場合、プロジェクトがクリーンにコンパイルすることを検証する必要があります。

この機能によって、開発環境に新しいバージョンの SDK とツールをインストールすることの決定と新しい言語機能をプロジェクトに組み込むことの決定が別になります。 ビルド コンピューターに最新の SDK とツールをインストールできます。 特定バージョンの言語をビルドに使用するように各プロジェクトを構成できます。

言語バージョンを設定する方法はいくつかあります。

- [Visual Studio のクイック アクション](#visual-studio-quick-action)を利用する。
- [Visual Studio UI](#set-the-language-version-in-visual-studio) で言語バージョンを設定する。
- [**.csproj** ファイルを手動で編集する](#edit-the-csproj-file)。
- [サブディレクトリ内の複数のプロジェクトに対して](#configure-multiple-projects)言語バージョンを設定する。
- [`-langversion` コンパイラ オプション](#set-the-langversion-compiler-option)を構成する。

## <a name="visual-studio-quick-action"></a>Visual Studio のクイック アクション

Visual Studio は、必要な言語バージョンを判断するのに役立ちます。 現在構成されているバージョンで使用できない言語機能を使用する場合、Visual Studio は、プロジェクトの言語バージョンを更新する可能性のある修正プログラムを示します。

## <a name="set-the-language-version-in-visual-studio"></a>Visual Studio で言語バージョンを設定する

Visual Studio のバージョンを設定できます。 ソリューション エクスプローラーでプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウン リストで、バージョンを選択します。 次の図は "最新の" 設定を示しています。

![言語バージョンを指定できる高度なビルド設定のスクリーン ショット](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Visual Studio IDE を使用して csproj ファイルを更新する場合、IDE によって、ビルド構成ごとにノードが作成されます。 一般的に、すべてのビルド構成で同じように値を設定しますが、ビルド構成ごとに明示的に設定する必要があります。あるいは、この設定を変更するとき、"すべての構成" を選択します。 csproj ファイルに次が表示されます。
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>csproj ファイルを編集する

**.csproj** ファイルで言語バージョンを設定できます。 次のような要素を追加します。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

値 `latest` は、C# 言語の最新のマイナー バージョンを使用します。 次の値を指定できます。

|[値]|説明|
|------------|-------------|
|default|コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。|
|ISO-1|コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます。 |
|ISO-2|コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます。 |
|3|コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます。|
|4|コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます。|
|5|コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます。|
|6|コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます。|
|7|コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます。|
|7.1|コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます。|
|7.2|コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます。|
|7.3|コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます。|
|latest|コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。|

特殊文字列の `default` と `latest` はそれぞれ、ビルド コンピューターにインストールされている最新のメジャー言語バージョン (C# 7.0) とマイナー言語バージョン (C# 7.3) に解決されます。

## <a name="configure-multiple-projects"></a>複数のプロジェクトを構成する

複数のディレクトリを構成する `<LangVersion>` 要素を含む **Directory.build.props** ファイルを作成することができます。 この操作は通常、ソリューション ディレクトリで実行します。 ソリューション ディレクトリ内の **Directory.build.props** ファイルに以下を追加します。

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

これで、そのファイルを含むディレクトリのすべてのサブディレクトリ内のビルドで、C# バージョン 7.3 構文が使用されます。 詳しくは、「[ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)」を参照してください。

## <a name="set-the-langversion-compiler-option"></a>言語コンパイラ オプションを設定する

`-langversion` コマンド ライン オプションを使用することができます。 詳しくは、[-langversion](../language-reference/compiler-options/langversion-compiler-option.md) コンパイラ オプションに関する記事を参照してください。 「`csc -langversion:?`」と入力して、有効な値の一覧を確認できます。
