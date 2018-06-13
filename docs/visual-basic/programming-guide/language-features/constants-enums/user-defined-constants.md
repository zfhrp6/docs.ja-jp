---
title: ユーザー定義定数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: b4a7e2b63b930b98ee082c0104c24f6857b5b35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648776"
---
# <a name="user-defined-constants-visual-basic"></a>ユーザー定義定数 (Visual Basic)
定数とは、数値または文字列が変化しないの代わりに使用されるわかりやすい名前です。 定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。 コントロールまたは使用するコンポーネントで定義されている定数を使用するか、独自に作成することができます。 自分で作成した定数は*ユーザー定義*です。  
  
 持つ定数を宣言する、`Const`ステートメントでは、変数名を作成する場合と同じガイドラインを使用します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
## <a name="const-statement-usage"></a>Const ステートメントの使用方法  
 A`Const`ステートメント、数学的表現したり、日付/時刻の数量。  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 定義できます`String`定数。  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 等号の右側にある式 ( `=` )、数値またはリテラル文字列は、多くの場合は、(ただし、その式には、関数への呼び出しを含めることはできません)、数値または文字列に評価される式を指定することもできます。 以前に定義された定数の観点から定数も定義できます。  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>ユーザー定義関数のスコープ  
 A`Const`ステートメントのスコープは同じ場所に宣言された変数と同じです。 次のような方法では、スコープを指定できます。  
  
-   プロシージャ内でのみ存在する定数を作成するには、そのプロシージャ内で宣言します。  
  
-   使用できるは、そのモジュールの外部コードではなく、クラス内のすべてのプロシージャに定数を作成するには、クラスの宣言セクションで宣言します。  
  
-   アセンブリの外部のクライアントではなく、アセンブリのすべてのメンバーには、使用できる定数を作成するには、宣言を使用して、`Friend`クラスの宣言セクション内のキーワードです。  
  
-   アプリケーション全体で使用できる定数の宣言を使用して、`Public`セクションで、クラスの宣言でキーワード。  
  
 詳細については、次を参照してください。[する方法: A 定数の宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)です。  
  
### <a name="avoiding-circular-references"></a>循環参照の回避  
 発生する可能性は他の定数の観点から定数を定義するため、*サイクル*、または 2 つ以上の定数との間の循環参照。 循環参照は、2 つ以上のパブリック定数、別の例を次の観点でそれぞれを定義した場合に発生します。  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 循環参照が発生した場合、Visual Basic は、コンパイラ エラーを生成します。  
  
## <a name="see-also"></a>関連項目  
 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [定数と列挙体](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
