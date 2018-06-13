---
title: Visual Basic におけるジェネリック プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649397"
---
# <a name="generic-procedures-in-visual-basic"></a>Visual Basic におけるジェネリック プロシージャ
A*ジェネリック プロシージャ*もという、*ジェネリック メソッド*、少なくとも 1 つの型パラメーターで定義されているプロシージャは、します。 これにより、呼び出し元のコードをプロシージャが呼び出されるたびに、その要求をデータ型を調整できます。  
  
 手順は、ジェネリック クラスまたはジェネリック構造体の内部で定義されていることだけでジェネリックではありません。 ジェネリックにするには、プロシージャはかかる場合があります、通常のパラメーターに加えて、少なくとも 1 つの型パラメーターを受け取る必要があります。 ジェネリック クラスまたは構造体は、非ジェネリック プロシージャは、および非ジェネリックのクラス、構造体を含めることができます、またはモジュールには、ジェネリック プロシージャが含まれていることができます。  
  
 ジェネリック プロシージャでは、戻り値の型、およびそのプロシージャのコードがある場合、通常のパラメーター リストにその型パラメーターを使用できます。  
  
## <a name="type-inference"></a>型推論  
 すべての型引数を指定せず、ジェネリック プロシージャを呼び出すことができます。 この方法で呼び出すこと、コンパイラは、プロシージャの型引数を渡すための適切なデータ型を決定しようとします。 これと呼ばれる*型推論*です。 次のコードが呼び出しを示しているコンパイラが推論型を渡すかで`String`、型パラメーターに`t`です。  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 場合は、コンパイラは、呼び出しのコンテキストから型引数を推定できません、エラーを報告します。 このようなエラーの考えられる原因の 1 つは、配列ランクの不一致です。 たとえば、型パラメーターの配列として、通常のパラメーターを定義します。 ジェネリック プロシージャを呼び出す場合は、異なるランク (次元の数) の配列を指定する、不一致が原因で型の推定が失敗します。 次のコードを 1 次元配列を受け取るプロシージャに渡される 2 次元配列にします。  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 型の推論は、すべての型引数を省略することによってのみ呼び出すことができます。 1 つの型引数を指定する場合は、それらすべてを指定する必要があります。  
  
 型の推定方法は、ジェネリック プロシージャにのみサポートされます。 ジェネリック クラス、構造体、インターフェイス、またはデリゲートの型の推論を呼び出すことはできません。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、汎用的な`Function`配列内の特定の要素を検索する手順。 1 つの型パラメーターを定義し、パラメーター リスト内の 2 つのパラメーターを構築するために使用します。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>コメント  
 前の例を比較することが必要に`searchValue`の各要素に対して`searchArray`です。 この機能を保証するために、型パラメーター制約`T`を実装する、<xref:System.IComparable%601>インターフェイスです。 コードを使用して、<xref:System.IComparable%601.CompareTo%2A>メソッドの代わりに、`=`演算子に渡される型引数の保証がないため`T`をサポートしている、`=`演算子。  
  
 テストすることができます、`findElement`次のコードを持つプロシージャ。  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 呼び出す前に、 `MsgBox` 「0」、「1」、および「-1」をそれぞれ表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [方法 : ジェネリック クラスを使用する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [手順](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [プロシージャのパラメーターと引数](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [型リスト](../../../../visual-basic/language-reference/statements/type-list.md)  
 [パラメーター リスト](../../../../visual-basic/language-reference/statements/parameter-list.md)
