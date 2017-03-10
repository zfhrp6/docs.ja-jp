---
title: "Constants Overview (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constants"
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Constants Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

定数とは、数字または文字列の代わりに使用される名前のことであり、その値は不変です。  定数に格納された値は、その名が示すとおり、アプリケーションの実行中に変わることはありません。  定数を使うとコードが読みやすくなり、保守も簡単になります。  定数は、コード内で、同じ値を繰り返し使用する場合や、覚えにくいか意味が明白でない特定の数値を参照する場合に使用します。  
  
## 定数の作成および使用方法  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には多数の定義済み定数があり、主として印刷用および表示用に使用されます。  定数は、変数名を作成するときと同じガイドラインに従って、`Const` ステートメントで宣言します。  `Option Strict` が `On` である場合、定数の型を明示的に宣言する必要があります。  
  
 定数のスコープ、つまり名前に修飾子を付けずに定数を参照できるコードの範囲は、同じ場所で変数を宣言した場合の変数のスコープと同じです。  特定のプロシージャのスコープ内で存在する定数を作成するには、定数をそのプロシージャ内で宣言します。  アプリケーション全体で使用できる定数の宣言は、クラスの宣言セクションで `Public` キーワードを使って行います。  
  
> [!NOTE]
>  定数は変数と似ていますが、変数のように変更することや新しい値を代入することはできません。  
  
 コードで使用する定数には、使用するコントロールやコンポーネントのオブジェクト モデルにあらかじめ用意されている定数と、ユーザー定義の定数 \(つまり、自分で作成する定数\) とがあります。  
  
## コンパイル時定数および実行時定数  
 コンパイル時定数は、コードがコンパイルされる時点で計算されます。一方、実行時定数は、アプリケーションの実行時にならないと計算できません。  コンパイル時定数の値はアプリケーションを何回実行しても常に同じですが、実行時定数の値はアプリケーション実行のたびに変わる可能性があります。  コンパイル時定数は、配列の上下限、ケース式、列挙子の初期化子などに必要です。  
  
## このセクションの内容  
  
|||  
|-|-|  
|定義|語句|  
|[How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|`Const` ステートメントを使用して定数を宣言し、定数に値を設定する方法を説明します。定数を宣言する際には、値を予想しやすい名前を割り当てます。|  
|[User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|独自の定数を作成する方法について説明します。スコープについて、および循環参照を避ける方法についても説明します。|  
|[Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|`Option Explicit` がオフの場合に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラが定数を初期化する方法について説明します。|  
|[How to: Group Related Constant Values Together](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|関連する定数の値をグループ化する方法を示します。|  
  
## 参照  
  
|||  
|-|-|  
|定義|語句|  
|[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] に定義済みの定数を一覧で示します。|  
|[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)|`Const` ステートメントとその使用方法について説明します。|  
|[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|`Option Strict` ステートメントとその使用方法について説明します。|  
  
## 参照  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)