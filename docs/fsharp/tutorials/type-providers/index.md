---
title: 型プロバイダー
description: F# 型プロバイダーの種類、プロパティ、およびプログラム内で使用するメソッドを提供するコンポーネントの方法について説明します。
ms.date: 04/02/2018
ms.openlocfilehash: 82d9afed7d77eae5f8b96854d40e96a32c4fae9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="type-providers"></a>型プロバイダー

F# 型プロバイダーは、プログラムで使用する型、プロパティ、およびメソッドを指定するコンポーネントです。 型プロバイダーとして知られる仕組みを生成する**指定された型が**、f# コンパイラによって生成され、外部データ ソースに基づきます。

たとえば、SQL の f# 型プロバイダーは、リレーショナル データベースのテーブルと列を表す型を生成できます。 これは実際には、どのような[SQLProvider](https://fsprojects.github.io/SQLProvider/)型プロバイダーはします。

種類は、型プロバイダーに渡す入力パラメーターによって異なります。 用意されています。 このような入力を JSON スキーマ ファイルなど)、サンプル データ ソースにすることができます、外部サービスまたはデータ ソースへの接続文字列を直接指す URL です。 型プロバイダーは、型のグループのみを展開するオンデマンドも確認できます。つまり、型が実際には、プログラムによって参照されている場合、展開されます。 これにより、オンライン データ マーケットのような大規模な情報空間の直接的な、必要に応じた統合を厳密に型指定された方法で実現できます。

## <a name="generative-and-erased-type-providers"></a>当初、消去型プロバイダー

型プロバイダーには 2 つの形式: 当初と消去されます。

生成的型プロバイダーは、.NET 型としては、生成されたアセンブリに書き込むことができる型を生成します。 これにより、それらを他のアセンブリ内のコードから使用することができます。 意味、データ ソースの型指定された形式を必要があります一般にいずれかの .NET 型で表すことは不可能です。

消去型プロバイダーは、アセンブリまたはプロジェクトが生成されるからでのみ利用できる型を生成します。 種類は短期です。アセンブリに書き込まれていない、他のアセンブリ内のコードでは使用できません。 含めることができる*遅れて*無数情報空間からの型を使用して提供しており、メンバーです。 これらは、大規模で相互接続されたデータ ソースの小さなサブセットを使用するため便利です。

## <a name="commonly-used-type-providers"></a>一般的に使用される型プロバイダー

広く使用されている次のライブラリは、さまざまな用途の型プロバイダーを含めます。

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/)型プロバイダーには JSON、XML、CSV、および HTML ドキュメントの形式とリソースが含まれています。
- [SQLProvider](https://fsprojects.github.io/SQLProvider/)を使用するオブジェクトのマッピングと f# LINQ リレーション データベースへのアクセスを厳密に型指定されたこれらのデータ ソースに対するクエリを提供します。
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)がコンパイル時の型プロバイダーの設定をオンに f# で T-SQL の埋め込み。
- [Azure のストレージ型プロバイダー](https://fsprojects.github.io/AzureStorageTypeProvider/) Azure Blob、テーブル、およびリソース名、プログラム全体で文字列として指定することがなくこれらのリソースにアクセスすることができますのキューの型を提供します。
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html)が含まれています、 **GraphQLProvider**URL で指定された GraphQL server ベースの型を提供します。

必要に応じて、することができます[独自のカスタム型プロバイダーを作成する](creating-a-type-provider.md)、または他のユーザーによって作成されている型プロバイダーを参照します。 たとえば、組織に 1 つのデータ サービスを用意し、そのデータ サービスにより、増加し続ける名前付きデータセット群と各データセットの安定したデータ スキーマを提供するとします。 スキーマを読み取り、利用可能な最新のデータセットを厳密に型指定してプログラマに提示する型プロバイダーを作成することもできます。

## <a name="see-also"></a>関連項目
[チュートリアル: 型プロバイダーを作成します。](creating-a-type-provider.md)

[F# 言語リファレンス](../../language-reference/index.md)

[Visual F#](../../index.md)
