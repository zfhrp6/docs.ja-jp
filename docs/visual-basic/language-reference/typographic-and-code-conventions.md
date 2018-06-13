---
title: 表記規則とコード規則 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: eb7a33ef21bf6beda730dffa8eb7ff9cabe599fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604498"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>表記規則とコード規則 (Visual Basic)
Visual Basic のドキュメントでは、次の文字体裁とコード規則を使用します。  
  
## <a name="typographic-conventions"></a>表記規則  
  
|例|説明|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|言語固有のキーワードとランタイムのメンバーは、先頭の大文字があるし、は、この例で示すように書式設定します。|  
|**SmallProject**、 **ButtonCollection**|この例で示すように、単語や語句を入力するように指示されますが書式設定します。|  
|[Module ステートメント](../../visual-basic/language-reference/statements/module-statement.md)|リンクをクリックすると別のヘルプ ページに移動することができますは、この例で示すように書式設定です。|  
|*オブジェクト*、 *variableName*、 `argumentList`|指定した情報のプレース ホルダーは、この例で示すようにフォーマットされます。|  
|[影]、[*から抜け出します*]|構文では、省略可能な項目は角かっこで囲まれます。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|構文では、2 つ以上の項目間の選択を行う必要があります項目中かっこで囲むし、が縦棒で区切られてです。<br /><br /> 1 つ、および 1 つだけ、項目を選択する必要があります。|  
|[ `Protected` &#124; `Friend` ]|構文では、2 つ以上の項目間を選択するオプションがある場合は、アイテムが角かっこで囲むし、縦棒で区切られてです。<br /><br /> アイテムの任意の組み合わせまたは項目を選択できません。|  
|[{ `ByVal` &#124; `ByRef` }]|構文では、2 つ以上の項目を選択できますが、項目を完全に省略することも、アイテムが角かっこ、中かっこで囲まれ、縦棒で区切られてで囲まれました。|  
|*memberName*1、 *memberName*2、 *memberName*3|同じプレース ホルダーの複数のインスタンスは、例のように、添字によって区別されます。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|省略記号 (...) の構文では、省略記号の直前の種類のアイテムの不特定数を示すために使用します。<br /><br /> コードでは、わかりやすく説明を省略するとコードを示します。|  
|ESC キーを入力してください|キー名とキーボードのキー シーケンスがすべて大文字で表示されます。|  
|ALT + F1|キー名の間に正符号 (+) が表示されたらは、他のキーを押しているときに 1 つのキーを押しながら必要があります。 たとえば、F1 キーを押しながら ALT キーを押しながら alt キーを押しながら f1 キーを意味します。|  
  
## <a name="code-conventions"></a>コード規則  
  
|例|説明|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|コード サンプルでは、固定ピッチ フォントで表示され、は、この例で示すように書式設定します。|  
|前のステートメントの値を設定する`sampleString`に「こんにちは, world!」|説明テキストでコード要素は、この例で示すようを固定ピッチ フォントで表示されます。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|コードのコメントはアポストロフィ (') または REM キーワードによって導入されました。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|アンダー スコア (_)、行の末尾にスペースは、次の行に、ステートメントを続行することを示します。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の言語リファレンス](../../visual-basic/language-reference/index.md)  
 [キーワード](../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic ランタイム ライブラリのメンバー](../../visual-basic/language-reference/runtime-library-members.md)  
 [Visual Basic の名前付け規則](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [方法 : コード内でステートメントを分割および連結する](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [コード内のコメント](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
