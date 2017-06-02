---
title: "Option Compare ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8b1b077a8818315e52ada6b08ff1e1ced9bbd17c
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="option-compare-statement"></a>Option Compare ステートメント
文字列データを比較するときに使用する既定の比較方法を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`Binary`|省略可能です。 文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。 この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。|  
|`Text`|省略可能です。 文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。 たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。|  
  
## <a name="remarks"></a>コメント  
 使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
 `Option Compare` ステートメントでは、文字列の比較方法 (`Binary` または `Text`) を指定します。  既定のテキスト比較方法は `Binary` です。  
  
 `Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。 `Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。  
  
 Microsoft Windows では、並べ替え順序はコード ページによって決まります。 詳細については、「[コード ページ](https://docs.microsoft.com/cpp/c-runtime-library/code-pages)」をご覧ください。  
  
 次の例では、英語/ヨーロッパ言語のコード ページ (ANSI 1252) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 
          `Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Option Compare ステートメントが指定されていない場合  
 ソース コードが含まれていない場合、`Option Compare`ステートメント、 **Option Compare**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。 設定が指定されたコマンド ライン コンパイラを使用する場合、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションを使用します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>IDE で Option Compare を設定するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、次を参照してください。 [NIB: プロジェクト デザイナーでプロジェクトのプロパティを管理する](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)です。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を設定、 **Option Compare**ボックス。  
  
 プロジェクトを作成するときに、 **Option Compare**の設定、**コンパイル**に設定されているタブ、 **Option Compare**で設定、**オプション** ダイアログ ボックス。 この設定を変更する、**ツール** メニューのをクリックして**オプション**します。 **オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、 をクリックし、 **VB が既定で**します。 初期の既定の設定**VB 既定**は**バイナリ**します。  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>コマンド ラインで Option Compare を設定するには  
  
-   含める、 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)コンパイラ オプションで、 **vbc**コマンドです。  
  
## <a name="example"></a>例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。 このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements #&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。 このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements&#46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)   
 [文字列関数](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
