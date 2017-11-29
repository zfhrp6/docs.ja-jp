---
title: "XML ドキュメント (F#)"
description: "コメントからドキュメントを生成するために、f# でサポートについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d99ab1b6-e170-4ec2-a543-43ea7ab15bb2
ms.openlocfilehash: 20768a7d4ea17c926318043f658691819a3d7d2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-documentation"></a>XML に関するドキュメント

トリプル スラッシュ (//) からのドキュメントを生成するコードで f# コメントです。 XML コメントには、コード ファイル (.fs) や (.fsi) の署名ファイル内の宣言が前に記述できます。


## <a name="generating-documentation-from-comments"></a>コメントからドキュメントを生成します。
コメントからドキュメントを生成するための f# でサポートは、他の .NET Framework 言語でと同じです。 その他の .NET Framework 言語と同様に、 [--doc コンパイラ オプション](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)Sandcastle などのツールを使用してドキュメントに変換できる情報を含む XML ファイルを生成することができます。 通常、他の .NET Framework 言語で記述されたアセンブリで使用するために設計されたツールを使用して、生成されたドキュメントでは、コンパイルされた f# の構成要素の形式に基づいている Api のビューを生成します。 ツール具体的に f# をサポートしない限り、これらのツールによって生成されたドキュメントは、f# の API のビューと一致しません。

XML からのドキュメントを生成する方法の詳細については、次を参照してください。 [XML ドキュメント コメント &#40;です。C &#35;です。プログラミング ガイド &#41;](https://msdn.microsoft.com/library/b2s063f7).


## <a name="recommended-tags"></a>推奨されるタグ
これには XML ドキュメント コメントを記述する 2 つの方法があります。 XML タグを使用せず、トリプル スラッシュ コメント内で直接ドキュメントを作成する 1 つです。 これを行う場合は、コメント テキスト全体が直後に続くコード コンス トラクターの概要ドキュメントとして取得されます。 各構成体の概要のみを記述する場合は、このメソッドを使用します。 その他の方法では、複数の構造化ドキュメントを提供する XML タグを使用してます。 2 番目のメソッドでは、概要、詳細説明、各パラメーターと型パラメーターと、スローされた例外のドキュメントおよび戻り値の説明を個別に指定することができます。 次の表では、f# の XML コード コメントで認識される XML タグについて説明します。



|タグの構文|説明|
|----------|-----------|
|**&lt;c&gt;***テキスト***&lt;/c&gt;**|指定する*テキスト*コードに示します。 このタグは、コードを適切なフォントでテキストを表示するドキュメント ジェネレーターが使用できます。|
|**&lt;概要&gt;***テキスト***&lt;/summary&gt;**|指定する*テキスト*プログラム要素の簡単な説明を示します。 説明は、通常、1 ~ 2 文です。|
|**&lt;「解説」&gt;***テキスト***&lt;/remarks&gt;**|指定する*テキスト*プログラム要素に関する補足情報が含まれています。|
|**&lt;param name ="***名前***"&gt;***説明***&lt;/param&gt;**|関数またはメソッド パラメーターの説明と名前を指定します。|
|**&lt;typeparam name ="***名前***"&gt;***説明***&lt;/typeparam&gt;**|名前と型パラメーターの説明を指定します。|
|**&lt;返します&gt;***テキスト***&lt;/returns&gt;**|指定する*テキスト*関数またはメソッドの戻り値について説明します。|
|**&lt;例外 cref ="***型***"&gt;***説明***&lt;/exception&gt;**|生成できる例外がスローされた場合の種類を指定します。|
|**&lt;cref を参照してください ="***参照***"&gt;***テキスト***&lt;/を参照してください&gt;**|別のプログラム要素へのインライン リンクを指定します。 *参照*されている XML ドキュメント ファイルに表示される名前です。 *テキスト*がリンクに表示されるテキストです。|
|**&lt;seealso cref ="***参照***"/&gt;**|別の型のドキュメントへの参照リンクを指定します。 *参照*されている XML ドキュメント ファイルに表示される名前です。 通常、ドキュメント ページの下部に表示されますへのリンクを参照してください。|
|**&lt;para&gt;***テキスト***&lt;/para&gt;**|段落のテキストを指定します。 これは内部のテキストを個別に使用、**解説**タグ。|

## <a name="example"></a>例

### <a name="description"></a>説明
シグネチャ ファイルの一般的な XML ドキュメント コメントを次に示します。


### <a name="code"></a>コード
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]
    
## <a name="example"></a>例

### <a name="description"></a>説明
次の例では、XML タグを持たない別の方法を示します。 この例では、コメント内のテキスト全体が概要と見なされます。 Summary タグを明示的に指定しないと場合、必要がありますいないを指定すること、その他のタグなど**param**または**返します**タグ。


### <a name="code"></a>コード
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[コンパイラ オプション](compiler-options.md)
