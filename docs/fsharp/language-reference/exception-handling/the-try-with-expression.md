---
title: "例外: try...with 式 (F#)"
description: "例外処理の f# 'try...with' 式を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36721076-95cd-4636-ae43-79dd512bee6c
ms.openlocfilehash: 163dfab49d4aaf23123800246fae2cad33e2257c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-trywith-expression"></a>例外: try...with 式

このトピックの内容について説明します、`try...with`式、f# 言語での例外処理に使用される式。


## <a name="syntax"></a>構文

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>コメント
`try...with` F# の例外を処理する式を使用します。 に似ていますが、 `try...catch` (C#) ステートメントです。 上記の構文のコードでは*expression1*例外を生成する可能性があります。 `try...with`式が値を返します。 正規表現全体がの値を返しますの例外がスローされない場合*expression1*です。 例外がスローされた場合、各*パターン*がさらに、例外とは、対応する、最初の一致するパターン、比較*式*と呼ばれる、*例外ハンドラー*、その分岐が実行され、式全体がその例外ハンドラーで、式の値を返します。 パターンが一致しない場合、例外は、一致するハンドラーが見つかるまで、呼び出し履歴を反映します。 例外ハンドラー内の各式から返される値の型が式から返される型と一致する必要があります、`try`ブロックします。

多くの場合、エラーが発生するという事実は、各例外ハンドラー内の式から返される有効な値がないことを意味します。 頻繁なパターンでは、オプション型である式の型を持つようにします。 次のコード例では、このパターンを示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外は、.NET 例外か f# の例外になることができます。 使用して、f# の例外を定義することができます、`exception`キーワード。

例外の種類とその他の条件でフィルター処理するさまざまなパターンを使用することができます。オプションは、次の表にまとめます。


|パターン|説明|
|-------|-----------|
|:? *例外の種類*|指定した種類の .NET 例外に一致します。|
|:? *例外の種類*として*識別子*|指定された .NET 例外の種類と一致するが、名前付きの値は、例外を示します。|
|*例外名*(*引数*)|F# の例外の種類に一致し、引数をバインドします。|
|*identifier*|任意の例外に一致し、例外オブジェクトに名前をバインドします。 等価**: しますか?として System.Exception***識別子*|
|*識別子*とき*条件*|条件が true の場合は、任意の例外と一致します。|

## <a name="examples"></a>例
次のコード例では、さまざまな例外ハンドラーのパターンの使用を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
`try...with`コンストラクトから個別の式では、`try...finally`式。 したがって、コードでは、両方が必要な場合、`with`ブロックと`finally`ブロック、2 つの式を入れ子にする必要があります。

>[!NOTE] 
使用することができます`try...with`非同期ワークフローでおよびその他のコンピュテーション式、する場合は、カスタマイズされたバージョンの`try...with`式を使用します。 詳細については、次を参照してください。[非同期ワークフロー](../asynchronous-workflows.md)、および[コンピュテーション式](../computation-expressions.md)です。


## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外の種類](exception-types.md)

[例外: `try...finally` 式](the-try-finally-expression.md)
