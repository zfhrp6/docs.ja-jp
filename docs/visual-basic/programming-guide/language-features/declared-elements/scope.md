---
title: Visual Basic におけるスコープ
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656296"
---
# <a name="scope-in-visual-basic"></a>Visual Basic におけるスコープ
*スコープ*一連の名前に修飾子またはを通じて使用できるようにせずに参照できるすべてのコードは、宣言された要素の[Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)です。 要素は、次のレベルのいずれかのスコープを持つことができます。  
  
|レベル|説明|  
|-----------|-----------------|  
|ブロック スコープ|宣言されたブロック、コード内でのみ使用可能|  
|プロシージャ スコープ|宣言されているプロシージャ内のすべてのコードで使用可能|  
|モジュール スコープ|モジュール、クラス、または構造体が宣言されているすべてのコードで使用可能|  
|Namespace スコープ|宣言されている名前空間内のすべてのコードに使用可能|  
  
 これらのレベルのスコープから進行状況を最も狭い (ブロック)、最も幅の広い (名前空間) に場所*狭いスコープ*修飾なしの要素に参照できるコードの最小セットのことを意味します。 詳細については、このページで「レベルのスコープ」を参照してください。  
  
## <a name="specifying-scope-and-defining-variables"></a>スコープを指定して、変数を定義します。  
 宣言する場合は、要素のスコープを指定します。 スコープは、次の要因によって異なります。  
  
-   要素を宣言する地域 (ブロック、プロシージャ、モジュール、クラスまたは構造体)  
  
-   要素の宣言を含む名前空間  
  
-   要素の宣言するアクセス レベル  
  
 これを行うために名前が同じで別のスコープを持つ変数を定義するときは注意して、予期しない結果に可能性があります。 詳細については、「 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## <a name="levels-of-scope"></a>スコープのレベル  
 プログラミング要素は、その宣言領域全体で使用できます。 同じリージョン内のすべてのコードは、その名前を修飾せず、要素を参照できます。  
  
### <a name="block-scope"></a>ブロック スコープ  
 ブロックは、開始および終了して、次のような宣言ステートメントで囲まれたステートメントのセットを示します。  
  
-   `Do` および `Loop`  
  
-   `For` [`Each`] と `Next`  
  
-   `If` および `End If`  
  
-   `Select` および `End Select`  
  
-   `SyncLock` および `End SyncLock`  
  
-   `Try` および `End Try`  
  
-   `While` および `End While`  
  
-   `With` および `End With`  
  
 ブロック内で変数を宣言する場合は、そのブロック内でのみ使用できます。 次の例では、整数型の変数のスコープで`cube`間ブロック`If`と`End If`を参照することが不要になったと`cube`ブロックからの実行のパスとします。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  変数のスコープは、ブロックに制限されている場合でもその有効期間はまだ全体のプロシージャのです。 処理中に、ブロックを複数回入力した場合、各ブロック変数は、前の値を保持します。 このようなケースで予期しない結果を回避するのには、ブロックの先頭でブロック変数を初期化することをお勧めします。  
  
### <a name="procedure-scope"></a>プロシージャ スコープ  
 プロシージャ内で宣言された要素では、そのプロシージャの外部使用できません。 宣言を含むプロシージャのみを使用できます。 このレベルでの変数とも呼ばれる*ローカル変数*です。 宣言することで、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、有無にかかわらず、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワード。  
  
 プロシージャとブロックのスコープは密接に関連します。 そのプロシージャ内で任意のブロックの外側ではなく、プロシージャ内部変数を宣言する場合は、プロシージャ全体をブロックがここでは、ブロック スコープを持つ、変数の考えることができます。  
  
> [!NOTE]
>  いる場合でも、すべてのローカル要素`Static`変数は、表示されている手順にプライベートです。 使用しているすべての要素を宣言することはできません、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)プロシージャ内でキーワード。  
  
### <a name="module-scope"></a>モジュール スコープ  
 便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造体に適用されます。 このレベルの要素を宣言するには、モジュール、クラスまたは構造体が、すべてのプロシージャまたはブロックの外部で宣言ステートメントを配置します。  
  
 モジュール レベルで宣言すると、選択したアクセス レベルは、スコープを決定します。 モジュール、クラスまたは構造体を含む名前空間もスコープに影響します。  
  
 要素が宣言した[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)アクセス レベルがある別のモジュール内のコードではなく、そのモジュール内のすべてのプロシージャにします。 `Dim`モジュール レベルのステートメントの既定値`Private`場合は、アクセス レベル キーワードを使用しないでください。 ただし、行うことができます、スコープとアクセス レベルより明確を使用して、`Private`キーワード、`Dim`ステートメントです。  
  
 次の例では、モジュールで定義されているすべてのプロシージャが文字列変数を参照できます`strMsg`です。 2 番目のプロシージャが呼び出されると、文字列変数の内容が表示されます`strMsg` ダイアログ ボックス。  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace スコープ  
 モジュールを使用してレベルにある要素を宣言する場合、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)要素が宣言されている名前空間全体ですべてのプロシージャを使用可能になったら、キーワード。 次の部分を変更前の例では、文字列変数に`strMsg`宣言の名前空間内の任意の場所のコードによって参照することができます。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace スコープには、入れ子になった名前空間が含まれています。 名前空間内で使用可能な要素もその名前空間内に入れ子に名前空間の中から使用できます。  
  
 いずれかのプロジェクトが含まれない場合[Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)s、プロジェクト内のすべてが同じ名前空間。 ここでは、名前空間のスコープはようなもののプロジェクト スコープ。 `Public` モジュール、クラス、または構造内の要素も、プロジェクトを参照する他のプロジェクトを使用できます。  
  
## <a name="choice-of-scope"></a>スコープの選択  
 変数を宣言するときにおく必要がありますに注意、次の点スコープを選択します。  
  
### <a name="advantages-of-local-variables"></a>ローカル変数の利点  
 ローカル変数は、次の理由ですべての種類の一時的な計算は、適切な選択を。  
  
-   **名前の競合回避します。** ローカルの変数名が競合を受けやすくなります。 たとえば、という名前の変数を含むいくつかの異なる手順を作成することができます`intTemp`です。 各いる限り`intTemp`各プロシージャが、独自のバージョンのみを認識する、ローカル変数として宣言されての`intTemp`します。 任意の 1 つのプロシージャは、ローカルの値を変更できます`intTemp`影響を与えずに`intTemp`他のプロシージャ内の変数です。  
  
-   **メモリ使用量。** ローカル変数は、そのプロシージャの実行中にのみ、メモリを消費します。 プロシージャが呼び出し元のコードに戻るときに、自らのメモリは解放されます。 これに対し、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)と[静的](../../../../visual-basic/language-reference/modifiers/static.md)変数、アプリケーションの実行が停止されるまで、メモリ リソースを消費するので、使用に必要な場合のみです。 *インスタンス変数*間メモリを消費、インスタンスが存在しているが、ローカル変数より効率的な可能性のあるより効率的`Shared`または`Static`変数。  
  
### <a name="minimizing-scope"></a>スコープを最小限に抑える  
 一般に、すべての変数または定数を宣言するとき、推奨されるプログラミング可能な幅の狭いスコープを作成することを (ブロック スコープは最も狭いです)。 これにより、メモリを節約できます、誤って間違った変数を参照する、コードの可能性を最小限に抑えられます。 同様に、ある変数を宣言する必要があります[静的](../../../../visual-basic/language-reference/modifiers/static.md)プロシージャ呼び出しの間には、その値を保持するために必要な場合のみです。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [方法: 変数のスコープを制御する](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
