---
title: "ユーザー定義定数 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e5942d8663a8866b2f9794a86756f2bf25660ba5
ms.lasthandoff: 03/13/2017

---
# <a name="user-defined-constants-visual-basic"></a>ユーザー定義定数 (Visual Basic)
定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。 定数値は、その名前からわかるように、一定に保たれるアプリケーションの実行中に格納します。 コントロールや使用するコンポーネントで定義されている定数を使用するか、独自に作成することができます。 自分で作成した定数は*ユーザー定義*します。  
  
 持つ定数の宣言、`Const`ステートメント、変数名を作成する場合と同じガイドラインを使用します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
## <a name="const-statement-usage"></a>Const ステートメントの使用状況  
 A`Const`ステートメント、数学的な表現したり、日付/時刻の数量。  
  
 [!code-vb[VbEnumsTask&#10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 定義できます`String`定数。  
  
 [!code-vb[VbEnumsTask&#13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 等号の右側にある式 ( `=` ) 多くの場合、数値またはリテラル文字列が、(ただし、その式には、関数の呼び出しを含めることはできません)、数値または文字列に評価される式を指定することもできます。 以前に定義された定数の観点から定数を定義することもできます。  
  
 [!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>ユーザー定義関数のスコープ  
 A`Const`ステートメントのスコープは、同じ場所で宣言された変数のと同じです。 次のような方法では、スコープを指定できます。  
  
-   プロシージャ内でのみ存在する定数を作成するには、そのプロシージャ内で宣言します。  
  
-   使用できるは、そのモジュールの外部コードではなく、クラス内のすべてのプロシージャに定数を作成するには、クラスの宣言セクションで宣言します。  
  
-   アセンブリの外部のクライアントではなく、アセンブリのすべてのメンバーには、使用できる定数を作成するには、宣言を使用して、`Friend`クラスの宣言セクションにキーワードです。  
  
-   アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`セクションで、クラスの宣言でキーワードです。  
  
 詳細については、次を参照してください。[方法: A 定数の宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)します。  
  
### <a name="avoiding-circular-references"></a>循環参照の回避  
 発生する可能性は他の定数の観点から定数を定義するため、*サイクル*、または&2; つ以上の定数の間での循環参照。 サイクルは、2 つ以上のパブリック定数は、別の例を次の条件で定義したときに発生します。  
  
 [!code-vb[VbEnumsTask&#16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask&17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 循環参照が発生した場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ エラーが発生します。  
  
## <a name="see-also"></a>関連項目  
 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [定数と列挙型](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [定数と列挙型](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
