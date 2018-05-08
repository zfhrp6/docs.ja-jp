---
title: オプション (F#)
description: 名前付きの値または変数の場合、実際の値の型が存在しない f# オプションを使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: c813c377af1db758a40efa2bd73de22cbb4c66f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="options"></a>オプション

名前付きの値または変数の実際の値が存在せず、f# でオプションの種類が使用されます。 オプション、基になる型があり、その型の値を保持できるか、値はない可能性があります。

## <a name="remarks"></a>コメント
次のコードは、オプションの種類を生成する関数を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

わかるように場合、入力`a`は 0 より大きく、`Some(a)`が生成されます。  それ以外の場合、`None`が生成されます。

値`None`オプションは、実際の値を持っていない場合に使用します。 それ以外の場合、式`Some( ... )`オプションの値を設定します。 値`Some`と`None`は、次の関数と同様に、パターン マッチで役立ちます`exists`を返す`true`オプションの値と`false`そうでない場合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>オプションを使用します。
オプションには検索に一致する結果が返されません場合によくを使用は、次のコードに示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

前のコードでは、一覧は、再帰的に検索です。 関数は、`tryFindMatch`は述語関数を受け取り`pred`を返すブール値、および検索するリスト。 述語を満たす要素が見つかった場合、再帰が終了し、関数の値を返します式でのオプション`Some(head)`です。 空のリストが一致すると、再帰は終了します。 値ではその時点で`head`が見つかりませんと`None`が返されます。

多数の f# ライブラリ関数も戻り値が存在しない可能性がある値のコレクションを検索する、`option`型です。 慣例により、これらの関数はで始まり、`try`プレフィックス、たとえば、 [ `Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)です。

値が存在しない場合に、たとえば、値を構築しようとすると、例外がスローされる可能性がある場合にでもオプションできますも役立ちます。 これを次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`関数前の例では型`string -> File option`を返すので、`File`オブジェクトのファイルが正常に開かれたかどうかと`None`例外が発生した場合。 状況に応じてある可能性がありますいないを適切な設計で選択を反映するのではなく、例外をキャッチします。


## <a name="option-properties-and-methods"></a>オプションのプロパティとメソッド
オプションの種類には、次のプロパティとメソッドがサポートしています。



|プロパティまたはメソッド|型|説明|
|------------------|----|-----------|
|[None](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|静的なプロパティを持つオプションの値を作成することができます、`None`値。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|返します`true`オプションがある場合、`None`値。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|返します`true`オプションのではない値が`None`です。|
|[いくつか](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|オプションを作成する静的メンバーではない値が指定されて`None`です。|
|[値](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|基になる値を返すかをスローした、`System.NullReferenceException`値が場合`None`です。|

## <a name="option-module"></a>Option モジュール
モジュールがある[オプション](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)オプションで操作を実行する便利な関数を格納しています。 一部の関数、プロパティの機能の繰り返しは役立ちますのコンテキストで関数が必要な場所。 [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)と[Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)オプション値を保持するかどうかをテストする両方のモジュール関数です。 [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)いずれかを使用する必要がある場合、値を取得します。 値がない場合スロー`System.ArgumentException`です。

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)関数は、値がある場合、値に関数を実行します。 関数が正確に 1 つの引数を受け取る必要があり、そのパラメーターの型は、オプションの型である必要があります。 関数の戻り値は、別のオプションの種類です。

Option モジュールには、リスト、配列、シーケンス、およびその他のコレクション型で利用可能な関数に対応する関数も含まれています。 これらの関数を含める[ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)、 [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191)、 [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428)、 [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99)、 [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)、 [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8)、および[ `Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)です。 これらの関数では、0 個または 1 つの要素のコレクションと同様に使用するオプションを有効にします。 詳細と例については、コレクション関数の説明を参照してください。[一覧](lists.md)です。


## <a name="converting-to-other-types"></a>その他の型に変換します。
オプションは、リストまたは配列に変換できます。 オプションは、これらのデータ構造のいずれかに変換するときに、結果として得られるデータ構造に 0 個または 1 つの要素があります。 オプションを配列に変換するには使用[ `Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)です。 オプションをリストに変換するには使用[ `Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)です。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[F# の型](fsharp-types.md)
