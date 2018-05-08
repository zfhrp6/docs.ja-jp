---
title: Visual Basic の名前付け規則
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic の名前付け規則
要素は、Visual Basic アプリケーションの名前、ときに、その名前の最初の文字は、文字は英字またはアンダー スコアにする必要があります。 ただし、アンダー スコアで始まる名前に準拠していないこと、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)。  
  
 次の提案は、名前付けに適用されます。  
  
-   としてでは大文字で名前の独立した各単語を開始`FindLastRecord`と`RedrawMyForm`です。  
  
-   開始、動詞を使用して、関数、およびメソッドの名前として`InitNameArray`または`CloseDialog`です。  
  
-   開始クラス、構造体、モジュール、および、名詞とプロパティ名として`EmployeeName`または`CarAccessory`です。  
  
-   プレフィックスが付いているインターフェイスを開始"I"、続けて名詞または名詞句の場合と同様に`IComponent`、またはインターフェイスの動作を説明するような形容詞`IPersistable`です。 および使用しないで、アンダー スコア、略語で混乱可能性があるために、慎重に、省略形を使用します。  
  
-   で始め、名詞が続くイベントの種類を説明するイベント ハンドラー名、"`EventHandler`「サフィックスで」`MouseEventHandler`"です。  
  
-   イベント引数クラスの名前が含まれる、"`EventArgs`"サフィックス。  
  
-   ある場合、イベントの概念"before"または"after"サフィックスで使用、現在時制または過去時制として"`ControlAdd`「または」`ControlAdded`"です。  
  
-   長であるか、または頻繁に使用される用語では、たとえば、"HTML"、「ハイパー テキスト マークアップ言語」ではなく、適切な名前の長さを保持する略語を使用します。 一般に、32 文字を超える変数の名前は画面解像度の低い設定読みにくくします。 また、省略形は、アプリケーション全体で一貫性のあることを確認してください。 "HTML"と「ハイパー テキスト マークアップ言語」の間でのプロジェクト内にランダムに切り替え、混乱を招く可能性があります。  
  
-   外側のスコープでの名前と同じである内部スコープでの名前を使用しないでください。 エラーは、不正な変数にアクセスした場合に発生します。 変数と同じ名前のキーワードの間の競合が発生した場合は、適切なタイプ ライブラリで前にキーワードを識別する必要があります。 たとえば、という名前の変数がある場合`Date`、組み込みを使用することができます`Date`関数を呼び出すことによってのみ<xref:System.DateTime.Date%2A?displayProperty=nameWithType>です。  
  
## <a name="see-also"></a>関連項目  
 [コード内の要素名としてのキーワード](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)
