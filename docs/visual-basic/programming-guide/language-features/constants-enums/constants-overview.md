---
title: "定数の概要 (Visual Basic) |Microsoft ドキュメント"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8004045d233da0db017b26b350743ad9f8d61845
ms.lasthandoff: 03/13/2017

---
# <a name="constants-overview-visual-basic"></a>定数の概要 (Visual Basic)
定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。 定数は、同じである、名前が示すように、アプリケーションの実行中の値を格納します。 大幅に、コードの読みやすさを向上し、定数を使用して管理しやすきます。 再表示される値を含むコード内を使用すると、特定の数値を記憶または明確な意味がないしにくいに依存します。  
  
## <a name="how-to-create-and-use-constants"></a>作成して、定数を使用する方法  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]印刷および表示するために主を使用して、定義済みの定数の数が含まれています。 持つ独自の定数を作成することも、`Const`ステートメントの場合と同じガイドラインを使用して、変数名を作成します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
 一連の名前を修飾せずに参照できるすべてのコードでは、定数のスコープは、同じ場所で宣言された変数と同じです。 特定のプロシージャのスコープ内に存在する定数を作成するには、そのプロシージャ内で宣言します。 アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`クラスの宣言セクションにキーワードです。  
  
> [!NOTE]
>  定数には、変数と似ていますに変更したり、変数のように、新しい値を代入することはできません。  
  
 コントロールやコンポーネントを使用するためのオブジェクト モデルでは、コードで使用する定数を定義できますか、ユーザー定義できます (つまり、自分で作成した)。  
  
## <a name="compile-time-and-run-time-constants"></a>コンパイル時と実行時定数  
 コンパイル時定数は、実行時定数は、アプリケーションの実行中にのみ計算するときに、コードのコンパイル時に計算されます。 コンパイル時定数では、実行時定数たびに変わる可能性があります中に、アプリケーションが実行されるたびに同じ値があります。 コンパイル時定数は、配列の範囲、case 式は、列挙子の初期化子などの場合に必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|定義|用語|  
|---|---|  
|[方法 : 定数を宣言する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|使用する方法について説明、`Const`定数を宣言し、その値を設定するステートメントは定数を宣言すると、値にわかりやすい名前を割り当てます。|  
|[ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|循環参照を回避する方法とスコープの設定に関する情報など、独自の定数を作成する方法について説明します。|  
|[定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|方法に関する情報を提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ定数の初期化時に`Option Explicit`は無効になっています。|  
|[方法 : 関連する定数値をまとめてグループ化する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|関連付けられている定数の値をグループ化する方法を示します。|  
  
## <a name="reference"></a>参照  
  
|定義|用語|  
|---|---|  
|[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)|定義済み定数[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。|  
|[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)|説明、`Const`ステートメントとその使用します。|  
|[Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|説明、`Option Strict`ステートメントとその使用します。|  
  
## <a name="see-also"></a>関連項目  
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [方法: Visual Basic で配列変数を初期化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
