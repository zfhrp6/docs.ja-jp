---
title: "プロパティまたは文字列の名前 (Visual Basic) を使用して、メソッドの呼び出し |Microsoft ドキュメント"
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
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
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
ms.openlocfilehash: 87af2816ba42e2901c53bec5e9c19f34c676ed5c
ms.lasthandoff: 03/13/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)
ほとんどの場合は、デザイン時にプロパティとオブジェクトのメソッドを検出し、それらを処理するコードを記述できます。 ただし、場合によっては、ご存じないオブジェクトのプロパティとメソッドを事前にまたはプロパティを指定するか、実行時にメソッドを実行するエンドユーザーを有効化の柔軟性、たい場合があります。  
  
## <a name="callbyname-function"></a>CallByName 関数  
 たとえば、オペレーターを COM コンポーネントに渡すことによって、ユーザーが入力した式を評価するクライアント アプリケーションについて考えてみましょう。 新しい演算子を必要とするコンポーネントを常に新しい関数を追加するとします。 標準のオブジェクトのアクセス方法を使用する場合は、再コンパイルし、新しい演算子を使用できるように、クライアント アプリケーションを再配布する必要があります。 これを回避するには、使用することができます、`CallByName`アプリケーションを変更することがなく、文字列として新しい演算子を渡す関数です。  
  
 `CallByName`関数では、実行時にプロパティまたはメソッドを指定する文字列を使用することができます。 署名、`CallByName`関数は、次のようになります。  
  
 *Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())  
  
 最初の引数*オブジェクト*、対象とするオブジェクトの名前を受け取ります。 *ProcedureName*引数には、呼び出されるメソッドまたはプロパティ プロシージャの名前を表す文字列。 *CallType*引数を呼び出すプロシージャの種類を表す定数。 メソッド (`Microsoft.VisualBasic.CallType.Method`)、読み込まれるプロパティ (`Microsoft.VisualBasic.CallType.Get`)、またはプロパティの設定 (`Microsoft.VisualBasic.CallType.Set`)。 *引数*の引数は省略可能な型の配列を受け取る`Object`プロシージャに引数を格納しています。  
  
 使用する`CallByName`からオブジェクトまたはクラスが、現在のソリューションには、最もよく使用される COM オブジェクトにアクセスする[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリ。  
  
 という名前のクラスを格納するアセンブリへの参照を追加すると仮定`MathClass`、という名前の新しい関数を持つ`SquareRoot`の次のコードを参照してください。  
  
 [!code-vb[VbVbalrOOP #&53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 アプリケーションでは、コントロールのどのメソッドが呼び出されると、引数にテキスト ボックス コントロールを使用できます。 たとえば場合、`TextBox1`に評価される式が含まれていて、`TextBox2`は関数の名前を入力するために使用を使えば、次のコードを呼び出す、`SquareRoot`で式に対して関数`TextBox1`:  
  
 [!code-vb[VbVbalrOOP #&54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 「64」を入力した場合`TextBox1`で"SquareRoot" `TextBox2`、しを呼び出す、`CallMath`プロシージャ、内の数値の平方根`TextBox1`が評価されます。 例のコードを呼び出す、 `SquareRoot` (必須の引数として評価される式を表す文字列を扱う) に機能し、「8」を返します`TextBox1`(の平方根 64)。 もちろん、ユーザーが入力に無効な文字列`TextBox2`文字列に、メソッドの代わりにプロパティの名前が含まれているか、メソッドに追加の必須の引数がある場合、実行時エラーが発生した場合は、です。 使用する場合は、堅牢なエラー処理コードを追加する必要がある`CallByName`これらやその他のエラーを予測します。  
  
> [!NOTE]
>  中に、`CallByName`関数がいくつかの場合に役立つこと、パフォーマンスに与える影響に対して有用性を比較検討する必要があります: を使用して`CallByName`プロシージャを呼び出すには、遅延バインディング呼び出しよりもわずかに低下します。 呼び出される繰り返し、このようなループ内で、関数を呼び出す場合`CallByName`パフォーマンスに重大な影響を及ぼします。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [オブジェクトの型の決定](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
