---
title: "User-Defined Constants (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constants, circular references"
  - "Const statement [Visual Basic], user-defined constants"
  - "user-defined constants"
  - "scope, constants"
  - "constants, user-defined"
  - "circular references between constants"
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# User-Defined Constants (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

定数とは、数字または文字列の代わりに使用される名前のことであり、その値は不変です。  定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。  使用するコントロールやコンポーネントによって定義されている定数を使用するか、または独自の定数を作成できます。  自分で作成した定数は、*ユーザー定義*と呼ばれます。  
  
 定数は、変数名を作成するときと同じガイドラインに従って、`Const` ステートメントで宣言します。  `Option Strict` が `On` である場合、定数の型を明示的に宣言する必要があります。  
  
## Const ステートメントの使用方法  
 `Const` ステートメントでは、数値および日付や時刻を表す値を定数の値にできます。  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 また、文字列型 \(`String`\) の定数も定義できます。  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 通常、等号 \(`=`\) の右側には数値またはリテラル文字列を指定しますが、数値または文字列に評価される式を指定することもできます。ただし、指定する式の中に関数の呼び出しを含めることはできません。  また、既に定義された定数を使って別の定数を定義することもできます。次に例を示します。  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## ユーザー定義定数のスコープ  
 `Const` ステートメントのスコープは、同じ場所で宣言される変数のスコープと同じです。  スコープは、次のいずれかの方法で指定できます。  
  
-   プロシージャ内だけで存在する定数の宣言は、そのプロシージャ内で行います。  
  
-   同じクラスのすべてのプロシージャで使用でき、ほかのモジュールでは使用できない定数の宣言は、クラスの宣言セクションで行います。  
  
-   アセンブリのすべてのメンバーが使用でき、アセンブリの外部のクライアントは使用できない定数の宣言は、クラスの宣言セクションで `Friend` キーワードを使って行います。  
  
-   アプリケーション全体で使用できる定数の宣言は、クラスの宣言セクションで `Public` キーワードを使って行います。  
  
 詳細については、「[How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)」を参照してください。  
  
### 循環参照の回避  
 定数の値は、他の定数を使って定義できるため、複数の定数の間で*循環参照*が発生する可能性があります。  循環参照は、次のように、複数のパブリック定数が互いに参照し合うと発生します。  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 循環参照があると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] でコンパイラ エラーが発生します。  
  
## 参照  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)