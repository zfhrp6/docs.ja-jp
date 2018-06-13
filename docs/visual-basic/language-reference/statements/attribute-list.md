---
title: 属性リスト (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604075"
---
# <a name="attribute-list-visual-basic"></a>属性リスト (Visual Basic)
宣言されたプログラミング要素に適用される属性を指定します。 複数の属性を指定するときは、コンマで区切ります。 1 つの属性の構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>指定項目  
 `attributemodifier`  
 ソース ファイルの先頭に適用される属性に必須です。 指定できます[アセンブリ](../../../visual-basic/language-reference/modifiers/assembly.md)または[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)です。  
  
 `attributename`  
 必須。 属性の名前。  
  
 `attributearguments`  
 任意。 この属性の位置指定引数の一覧です。 複数の引数は、コンマで区切られます。  
  
 `attributeinitializer`  
 任意。 この属性の変数またはプロパティの初期化子の一覧です。 複数の初期化子は、コンマで区切られます。  
  
## <a name="remarks"></a>コメント  
 (型、プロシージャ、プロパティ、およびなど)、ほぼすべてのプログラミング要素には、1 つまたは複数の属性を適用できます。 属性がアセンブリのメタデータに表示され、コードに注釈を付けるか、特定のプログラミング要素を使用する方法を指定するのに役立ちます。 Visual Basic と .NET Framework によって定義された属性を適用して、独自の属性を定義することができます。  

 属性を使用する場合の詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)です。 詳細については、属性名は、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **配置します。** 最も宣言されたプログラミング要素に属性を適用できます。 配置する 1 つまたは複数の属性を適用する、*属性ブロック*要素宣言の先頭にします。 属性の一覧内の各エントリには、適用する属性および修飾子と属性のこの呼び出しを使用している引数を指定します。  
  
-   **山かっこです。** 属性リストを指定する場合は、山かっこで囲む必要があります ("`<`「と」`>`") です。  
  
-   **宣言の一部です。** 属性は、個別のステートメントではなく、要素の宣言の一部である必要があります。 行連結シーケンスを使用することができます (" `_`") を複数のソース コード行に、宣言ステートメントを拡張します。  
  
-   **修飾子です。** 属性の修飾子 (`Assembly`または`Module`)、ソース ファイルの先頭のプログラミング要素に適用されるすべての属性が必要です。 属性の修飾子は、ソース ファイルの先頭には存在しない要素に適用される属性では許可されません。  
  
-   **引数。** 属性のすべての位置指定引数には、任意の変数またはプロパティの初期化子が前に指定する必要があります。  
  
## <a name="example"></a>例  
 次の例に適用されます、<xref:System.Runtime.InteropServices.DllImportAttribute>属性のスケルトン定義を`Function`プロシージャです。  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 属性付きの手順がアンマネージ ダイナミック リンク ライブラリ (DLL) のエントリ ポイントを表すことを示します。 属性は、位置指定引数として DLL 名と変数の初期化子とその他の情報を提供します。  
  
## <a name="see-also"></a>関連項目  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Module \<キーワード>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
