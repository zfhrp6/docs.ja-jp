---
title: "プロジェクトを整理し、.NET Framework と .NET Core をサポートする"
description: "プロジェクトを整理し、.NET Framework と .NET Core をサポートする"
keywords: .NET, .NET Core
author: conniey
ms.author: mairaw
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
translationtype: Human Translation
ms.sourcegitcommit: 405bac1faa446687a4acdcf2d5536ee31f31f246
ms.openlocfilehash: b86693b1d6eed0ff5b8d1831e324354241f29806
ms.lasthandoff: 03/15/2017

---

# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>プロジェクトを整理し、.NET Framework と .NET Core をサポートする

> [!WARNING]
> このトピックはまだ更新されておらず、最新版のツールが反映されていません。

この記事は、プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。  プロジェクトを整理するためのオプションを提供し、開発者を支援します。  ここでは、.NET Core でプロジェクト レイアウトを設定する方法について決定するときに考慮する典型的なシナリオを紹介します。  プロジェクトのニーズに基づいて選択されており、すべてを網羅していないかもしれません。

* [**既存のプロジェクトと .NET Core プロジェクトを結合し、シングル プロジェクトを作成する**][option-xproj]
  
  *効果:*
  * 複数のプロジェクトをコンパイルするのではなく、シングル プロジェクトをコンパイルすることでビルド プロセスをシンプルにします。それぞれ、異なる .NET Framework バージョンまたはプラットフォームをターゲットにします。
  * ターゲットが複数のプロジェクトのソース ファイル管理をシンプルにします。シングル プロジェクト ファイルを管理することになります。  ソース ファイルの追加/削除時、代替方法では、これらを他のプロジェクトと手動で同期する必要があります。
  * 使用する NuGet パッケージを簡単に生成します。
  * コンパイラ ディレクティブを利用することで、ライブラリの特定の .NET Framework バージョンに対してコードを記述できます。
  
  *サポートされていないシナリオ:*
  * Visual Studio 2015 を持っていない開発者は既存のプロジェクトを開くことができません。 旧バージョンの Visual Studio をサポートするには、[プロジェクト ファイルを異なるフォルダーで保持する](#support-vs)ことが推奨されます。
  * 同じソリューション ファイルの異なるプロジェクト ファイルをまたいで .NET Core ライブラリを共有することはできません。 これをサポートするには、[ポータブル クラス ライブラリを作成する](#support-pcl)ことが推奨されます。
  * MSBuild のターゲットやタスクでサポートされるプロジェクト ビルドや読み込み変更は許可されません。 これをサポートするには、[ポータブル クラス ライブラリを作成する](#support-pcl)ことが推奨されます。

* <a name="support-vs"></a>[**既存のプロジェクトと新しい .NET Core プロジェクトを別々に保存する**][option-xproj-folder]
  
  *効果:*
  * 既存のプロジェクトで引き続き開発をサポートします。Visual Studio 2015 を所有していない開発者/貢献者はアップグレードする必要がありません。
  * 既存のプロジェクトで新しいバグが発生する可能性が減ります。既存のプロジェクトではコード チャーンが要求されないためです。

* <a name="support-pcl"></a>[**既存のプロジェクトを保持し、.NET Core をターゲットにするポータブル クラス ライブラリ (PCL) を作成する**][option-pcl]

  *効果:*
  * デスクトップまたは Web プロジェクトで .NET Core ライブラリを参照し、同じソリューションの完全 .NET Framework をターゲットにします。
  * プロジェクト ビルドまたは読み込みプロセスで変更をサポートします。 変更とは、たとえば、`*.csproj` ファイルに MSBuild のタスクやターゲットを追加することです。

  *サポートされていないシナリオ:*
  * 特定の .NET Framework バージョンのコードを記述することはできません。[定義プリプロセッサ記号][how-to-multitarget]がサポートされていないためです。

## <a name="example"></a>例

次のリポジトリを考慮してください。

![既存のプロジェクト][example-initial-project]

[**ソース コード**][example-initial-project-code]

下に説明する既存のプロジェクトの制約や複雑性にもよりますが、このリポジトリのために .NET Core のサポートを追加する方法がいくつかあります。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project-xproj"></a>既存のプロジェクトとターゲットが複数ある .NET Core Project (xproj) を置換します

リポジトリを再整理できます。既存の `*.csproj` ファイルが削除され、複数のフレームワークをターゲットにするシングル `*.xproj` ファイルが作成されます。  異なるフレームワークに対してシングル プロジェクトでコンパイルできるので、この方法が推奨されます。  さまざまなコンパイル オプション、依存関係などを処理することもできます。 対象のフレームワークごとに。

![複数のフレームワークをターゲットにする xproj の作成][example-xproj]

[**ソース コード**][example-xproj-code]

注目するべき変更点:
* `global.json` の追加
* `packages.config` および `*.csproj` を `project.json` および `*.xproj` に置換
* [Car の project.json][example-xproj-projectjson] とその[テスト プロジェクト][example-xproj-projectjson-test] を、既存の .NET Framework などのビルドをサポートするように変更

## <a name="create-a-portable-class-library-pcl-to-target-net-core"></a>ポータブル クラス ライブラリ (PCL) を作成し、.NET Core をターゲットにします。

既存のプロジェクトの `*.csproj` ファイルに複雑なビルド操作やプロパティが含まれる場合、PCL を簡単に作成できることがあります。

![][example-pcl]

[**ソース コード**][example-pcl-code]

注目するべき変更点:
*  `project.json` の名前を `{project-name}.project.json` に変更
    * これにより、Visual Studio で、同じディレクトリのライブラリのパッケージを復元しようとしたときの競合が回避されます。 詳細については、[NuGet FAQ](https://docs.nuget.org/consume/nuget-faq#working-with-packages) の "_I have multiple projects in the same folder, how can I use separate packages.config or project.json files for each project?_" (同じフォルダーに複数のプロジェクトがあります。プロジェクトごとに別々の packages.config ファイルまたは project.json ファイルを利用できますか。) を参照してください。
    *  **代替方法**: 別のフォルダーで PCL を作成し、元のソース コードを参照することでこの問題を回避します。  別のフォルダーに PCL を置くことには長所があります。Visual Studio 2015 を所有していないユーザーも新しいソリューションを読み込まずに古いプロジェクトを使用できます。
*  PCL の作成後、.NET Standard をターゲットにするには、Visual Studio で、**プロジェクトのプロパティ**を開きます。 **[ターゲット]** セクションで、**"Target .NET Platform Standard"** (.NET Platform Standard をターゲットにする) リンクをクリックします。  同じ手順を繰り返せば、この変更を元に戻すことができます。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>既存のプロジェクトを保持し、.NET Core プロジェクトを作成します

古いフレームワークをターゲットにする既存のプロジェクトがあるとき、そのようなプロジェクトをそのまま残し、.NET Core プロジェクトを利用して今後のフレームワークをターゲットにすると効率的な場合があります。

![別のフォルダーに既存の PCL がある .NET Core プロジェクト][example-xproj-different-folder]

[**ソース コード**][example-xproj-different-code]

注目するべき変更点:
* .NET Core と既存のプロジェクトを別々のフォルダーに保存します。
    * これにより、複数の project.json/package.config ファイルが同じフォルダーに存在することに起因する前述のパッケージ復元問題が回避されます。
    * プロジェクトを別々のフォルダーに保存すれば、(project.json により) Visual Studio 2015 を所有する必要がありません。  古いプロジェクトだけを開く別個のソリューションを作成できます。

## <a name="see-also"></a>関連項目

project.json と xproj に移行する方法に関する詳細については、[.NET Core の移植に関するドキュメント][porting-doc]のページを参照してください。

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "既存のプロジェクト"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-xproj]: media/project-structure/project.xproj.png "複数のフレームワークをターゲットにする xproj の作成"
[example-xproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/
[example-xproj-projectjson]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/src/Car/project.json
[example-xproj-projectjson-test]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj/tests/Car.Tests/project.json

[example-xproj-different-folder]: media/project-structure/project.xproj.different.png "別のフォルダーに既存の PCL がある .NET Core プロジェクト"
[example-xproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-xproj-keep-csproj/

[example-pcl]: media/project-structure/project.pcl.png ".NET Core をターゲットにする PCL"
[example-pcl-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-pcl

[option-xproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project-xproj
[option-pcl]: #create-a-portable-class-library-pcl-to-target-net-core
[option-xproj-folder]: #keep-existing-projects-and-create-a-net-core-project

[how-to-multitarget]: ../tutorials/libraries.md#how-to-multitarget

