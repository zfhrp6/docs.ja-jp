---
title: プロジェクトを整理し、.NET Framework と .NET Core をサポートする
description: プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.openlocfilehash: e6cd9c6d66996d9fd24fe71d48091723143e5849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211440"
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a>プロジェクトを整理し、.NET Framework と .NET Core をサポートする

この記事は、プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。 プロジェクトを整理するためのオプションを提供し、開発者を支援します。 次の一覧で、.NET Core でプロジェクト レイアウトを設定する方法について決定するときに考慮する典型的なシナリオを紹介します。 この一覧はプロジェクトのニーズに基づいて選択されており、すべてを網羅しるわけではりません。

* [**既存のプロジェクトと .NET Core プロジェクトを結合し、シングル プロジェクトを作成する**][option-csproj]

  *効果:*
  * 複数のプロジェクトをコンパイルするのではなく、シングル プロジェクトをコンパイルすることでビルド プロセスをシンプルにします。それぞれ、異なる .NET Framework バージョンまたはプラットフォームをターゲットにします。
  * ターゲットが複数のプロジェクトのソース ファイル管理をシンプルにします。シングル プロジェクト ファイルを管理することになります。 ソース ファイルの追加/削除時、代替方法では、これらを他のプロジェクトと手動で同期する必要があります。
  * 使用する NuGet パッケージを簡単に生成します。
  * コンパイラ ディレクティブを利用することで、ライブラリの特定の .NET Framework バージョンに対してコードを記述できます。

  *サポートされていないシナリオ:*
  * 既存のプロジェクトを開くには、開発者が Visual Studio 2017 を使用している必要があります。 旧バージョンの Visual Studio をサポートするには、[プロジェクト ファイルを異なるフォルダーで保持する](#support-vs)ことが推奨されます。

* <a name="support-vs"></a>[**既存のプロジェクトと新しい .NET Core プロジェクトを別々に保存する**][option-csproj-folder]

  *効果:*
  * 既存のプロジェクトで引き続き開発をサポートします。Visual Studio 2017 を所有していない開発者/貢献者はアップグレードする必要がありません。
  * 既存のプロジェクトで新しいバグが発生する可能性が減ります。既存のプロジェクトではコード チャーンが要求されないためです。

## <a name="example"></a>例

次のリポジトリを考慮してください。

![既存のプロジェクト][example-initial-project]

[**ソース コード**][example-initial-project-code]

下に説明する既存のプロジェクトの制約や複雑性にもよりますが、このリポジトリのために .NET Core のサポートを追加する方法がいくつかあります。

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>既存のプロジェクトとターゲットが複数ある .NET Core Project を置換します

リポジトリを再整理できます。既存の *\*.csproj* ファイルが削除され、複数のフレームワークをターゲットにするシングル *\*.csproj* ファイルが作成されます。 異なるフレームワークに対してシングル プロジェクトでコンパイルできるので、この方法が推奨されます。 さまざまなコンパイル オプション、ターゲットにするフレームワークごとの依存関係などを処理することもできます。

![複数のフレームワークをターゲットにする csproj の作成][example-csproj]

[**ソース コード**][example-csproj-code]

注目するべき変更点:
* *packages.config* と *\*.csproj* が新しい [.NET Core *\*.csproj*][example-csproj-netcore] に置き換わりました。 NuGet パッケージが `<PackageReference> ItemGroup` で指定されています。

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>既存のプロジェクトを保持し、.NET Core プロジェクトを作成する

古いフレームワークをターゲットにする既存のプロジェクトがあるとき、そのようなプロジェクトをそのまま残し、.NET Core プロジェクトを利用して今後のフレームワークをターゲットにすると効率的な場合があります。

![別のフォルダーに既存のプロジェクトがある .NET Core プロジェクト][example-csproj-different-folder]

[**ソース コード**][example-csproj-different-code]

注目するべき変更点:
* .NET Core と既存のプロジェクトを別々のフォルダーに保存します。
    * プロジェクトを別々のフォルダーに保存すれば、Visual Studio 2017 を所有する必要がありません。 古いプロジェクトだけを開く別個のソリューションを作成できます。

## <a name="see-also"></a>参照

.NET Core に移行する方法の詳細なガイダンスについては、[.NET Core の移植に関するドキュメント][porting-doc]のページを参照してください。

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "既存のプロジェクト"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "複数のフレームワークをターゲットにする csproj の作成"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "別のフォルダーに既存の PCL がある .NET Core プロジェクト"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
