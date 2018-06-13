---
title: 文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 76be426049489bb58e50878822c03fa5cd5cca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649228"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)
ほとんどの場合は、デザイン時に、プロパティとオブジェクトのメソッドを検出し、それらを処理するコードを記述できます。 ただし、場合によっては、知らない可能性オブジェクトのプロパティとメソッドを事前にもプロパティを指定するか、実行時にメソッドを実行するエンドユーザーの有効化の柔軟性をするだけです。  
  
## <a name="callbyname-function"></a>CallByName 関数  
 たとえば、COM コンポーネントに演算子を渡すことによって、ユーザーが入力した式を評価するクライアント アプリケーションを検討します。 新しい演算子を必要とするコンポーネントを常に新しい関数を追加するとします。 標準のオブジェクトのアクセス方法を使用する場合は、再コンパイルされ、新しい演算子を使用できるようにする前に、クライアント アプリケーションを再配布する必要があります。 これを回避するには、使用することができます、`CallByName`アプリケーションを変更することがなく、文字列として新しい演算子を渡す関数。  
  
 `CallByName`関数では、実行時にプロパティまたはメソッドを指定する文字列を使用することができます。 署名、`CallByName`関数は、次のようになります。  
  
 *結果* = `CallByName`(*オブジェクト*、 *ProcedureName*、 *CallType*、*引数*())  
  
 最初の引数は*オブジェクト*、対象とするオブジェクトの名前を取得します。 *ProcedureName*引数には、呼び出されるメソッドまたはプロパティ プロシージャの名前を表す文字列。 *CallType*引数には、プロシージャを呼び出すための型を表す定数: メソッド (`Microsoft.VisualBasic.CallType.Method`)、読み取りプロパティ (`Microsoft.VisualBasic.CallType.Get`)、またはプロパティの設定 (`Microsoft.VisualBasic.CallType.Set`)。 *引数*引数は省略可能、これは、型の配列を受け取る`Object`プロシージャに引数を格納しています。  
  
 使用することができます`CallByName`が、現在のソリューション内のクラスでは、最もよく使用される COM オブジェクトへのアクセスからオブジェクトまたは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリ。  
  
 という名前のクラスを格納するアセンブリへの参照を追加すると仮定します`MathClass`、という名前の新しい関数を持つ`SquareRoot`次のコードに示すように、します。  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 アプリケーションでは、コントロールのどのメソッドが呼び出されると、引数にテキスト ボックス コントロールを使用できます。 たとえば場合、`TextBox1`に評価される式を表すと`TextBox2`は関数の名前を入力するために使用、することができますを使用して、次のコードを呼び出す、`SquareRoot`関数内の式に`TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 「64」に入力した場合`TextBox1`、"SquareRoot"で`TextBox2`を呼び出すと、`CallMath`プロシージャ、内の数値の平方根`TextBox1`が評価されます。 この例のコードを呼び出す、 `SquareRoot` (必須の引数として評価される式を含む文字列を扱う) に機能し、「8」を返します`TextBox1`(の平方根 64)。 もちろん、ユーザー入力に無効な文字列`TextBox2`文字列は、メソッドの代わりに、プロパティの名前を含むメソッドに追加の必須引数がある場合、実行時エラーが発生した場合は、します。 使用する場合は、堅牢なエラー処理コードを追加する必要がある`CallByName`これらまたはその他のエラーを予測します。  
  
> [!NOTE]
>  中に、`CallByName`関数がいくつかのケースで役に立ちます、パフォーマンスに与える影響に対してその有用性を比較検討する必要があります: を使用して`CallByName`でプロシージャを呼び出すには、遅延バインディング呼び出しよりもわずかに遅くなります。 繰り返し呼び出されます、このようなループ内に関数を呼び出す場合`CallByName`パフォーマンスに重大な影響を持つことができます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [オブジェクトの型の決定](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
