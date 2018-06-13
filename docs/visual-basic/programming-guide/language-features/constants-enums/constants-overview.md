---
title: 定数の概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2ec43254013df5444048b5197489c55217d5328a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648386"
---
# <a name="constants-overview-visual-basic"></a>定数の概要 (Visual Basic)
定数とは、数値または文字列が変化しないの代わりに使用されるわかりやすい名前です。 定数は、同じである、名前が示すように、アプリケーションの実行中の値を格納します。 大幅に、コードの読みやすさを向上し、定数を使用して管理しやすくできます。 再度表示される値を含むコード内を使用すると、保存または明確な意味がないが困難な特定の番号によって異なります。  
  
## <a name="how-to-create-and-use-constants"></a>作成して、定数を使用する方法  
 Visual Basic には、主に印刷と表示を使用する定義済みの定数の数が含まれています。 持つ独自の定数を作成することも、`Const`ステートメントでは、変数名を作成する場合と同じガイドラインを使用します。 場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。  
  
 名前を修飾せずに参照できるすべてのコードのセットである、定数のスコープでは、同じ場所に宣言された変数のと同じです。 特定のプロシージャのスコープ内に存在する定数を作成するには、そのプロシージャ内で宣言します。 アプリケーション全体で使用できる定数の宣言を使用して、`Public`クラスの宣言セクション内のキーワードです。  
  
> [!NOTE]
>  定数には、変数と似ていますに変更したり、変数にすることができますに新しい値を代入することはできません。  
  
 コントロールやコンポーネントを使用するためのオブジェクト モデルによって、コードで使用する定数を定義できますも、ユーザー定義できます (つまり、自分で作成した)。  
  
## <a name="compile-time-and-run-time-constants"></a>コンパイル時と実行時の定数  
 コンパイル時定数は、実行時の定数は、アプリケーションの実行中にのみ計算するときに、コードのコンパイル時に計算されます。 コンパイル時定数は、アプリケーションが実行されるたび、そのたびに変化する可能性があります、実行時の定数に同じ値になります。 コンパイル時の定数は、配列の範囲、case 式は、列挙子の初期化子などの場合も必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|定義|用語|  
|---|---|  
|[方法 : 定数を宣言する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|使用する方法について説明します、`Const`ステートメント定数を宣言し、その値を設定する定数を宣言するには、値にわかりやすい名前を割り当てます。|  
|[ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|循環参照を回避する方法とスコープの設定に関する情報など、独自の定数を作成する方法について説明します。|  
|[定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Visual Basic コンパイラでの定数の初期化方法に関する情報を提供時に`Option Explicit`がオフになっています。|  
|[方法 : 関連する定数値をまとめてグループ化する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|関連付けられている定数の値をグループ化する方法を示します。|  
  
## <a name="reference"></a>参照  
  
|定義|用語|  
|---|---|  
|[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Visual Basic での定義済み定数を一覧表示します。|  
|[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)|について説明します、`Const`ステートメントとその使用します。|  
|[Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|について説明します、`Option Strict`ステートメントとその使用します。|  
  
## <a name="see-also"></a>関連項目  
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
