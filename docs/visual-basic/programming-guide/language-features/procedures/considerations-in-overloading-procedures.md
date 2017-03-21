---
title: "プロシージャ (Visual Basic) のオーバー ロードに関する考慮事項 |Microsoft ドキュメント"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: aa20cf367fba157f88afd861a4799540dcdecde1
ms.lasthandoff: 03/13/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>プロシージャのオーバーロードに関する注意事項 (Visual Basic)
プロシージャをオーバー ロードする場合、さまざまなを使用*署名*オーバー ロードされたバージョンごとにします。 つまり、通常各バージョンは、異なるパラメーター リストを指定する必要があります。 詳細については、「別の署名」を参照してください[プロシージャのオーバー ロード](./procedure-overloading.md)します。  
  
 オーバー ロードすることができます、`Function`プロシージャを`Sub`プロシージャ、その逆の場合は、異なるシグネチャを持つを提供します。 2 つのオーバー ロードできませんとは異なりのみ戻り値を持つ&1; つと持たないもう一方のです。  
  
 手順については、オーバー ロードするのと同様に、プロパティをオーバー ロードでき、同じ制限があります。 ただし、プロシージャをオーバー ロードできない、プロパティを使用して、またはその逆です。  
  
## <a name="alternatives-to-overloaded-versions"></a>オーバー ロードされたバージョンの代替手段  
 引数は省略可能なまたはその数が可変ときに特ににも、オーバー ロードされたバージョンの代替手段がある場合があります。  
  
 省略可能な引数が必ずしもすべての言語でサポートされていませんし、パラメーター配列に限定されることに注意してください[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。 複数の異なる言語のいずれかで記述されたコードから呼び出されると思われるプロシージャを作成する場合に、バージョンによって柔軟性がオーバー ロードされます。  
  
### <a name="overloads-and-optional-arguments"></a>省略可能な引数とオーバー ロード  
 呼び出し元のコードの指定または&1; つまたは複数の引数を省略できます必要に応じて場合、は、複数のオーバー ロードされたバージョンを定義するか、省略可能なパラメーターを使用します。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードが省略可能な引数を提供するかどうかどうかによって大きく異なります。  
  
-   プロシージャのコードは、呼び出し元のコードには、省略可能な引数が指定されているかどうかを確実にテストできません。 これは、大文字と小文字などの既定値の値、候補になる可能性がない場合、呼び出し元コードいないと考えられるを指定します。  
  
#### <a name="when-to-use-optional-parameters"></a>省略可能なパラメーターを使用する場合  
 次の場合に&1; つまたは複数の省略可能なパラメーターをすることができます。  
  
-   呼び出し元のコードは省略可能な引数を指定しない場合にのみ必要なアクションでは、既定値にパラメーターを設定します。 このような場合は、プロシージャのコードを単純化できますと&1; つ以上の&1; つのバージョンを定義する場合`Optional`パラメーター。  
  
 詳細については、次を参照してください。[省略可能なパラメーター](./optional-parameters.md)します。  
  
### <a name="overloads-and-paramarrays"></a>Paramarray とオーバー ロード  
 呼び出し元のコードでは、可変個の引数を渡すことができる場合、は、複数のオーバー ロードされたバージョンを定義するか、パラメーター配列を使用します。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。  
  
-   呼び出し元のコードことはありませんが合格する少数の値を超えるパラメーターの配列にわかります。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードに渡す値の数によって大きく異なります。  
  
-   呼び出し元のコードでは、異なるデータ型の値を渡すことができます。  
  
#### <a name="when-to-use-a-parameter-array"></a>パラメーター配列を使用する場合  
 方が適している、`ParamArray`パラメーターは、次の場合。  
  
-   呼び出し元のコードは、パラメーターの配列を渡すことができます値の数を予測できないし、数が多い可能性があります。  
  
-   プロシージャのロジックは、呼び出し元のコードを渡すと、すべての値に同じ操作を実行するすべての値を反復処理に適しています。  
  
 詳細については、次を参照してください。[パラメーター配列](./parameter-arrays.md)します。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>省略可能なパラメーターの暗黙のオーバー ロード  
 使用してプロシージャを[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメータは、省略可能なパラメーターを持つと&2; つのオーバー ロードされたプロシージャに相当します。 これらのいずれかに対応する、パラメーター リストでこのようなプロシージャをオーバー ロードすることはできません。 次の宣言では、これを示しています。  
  
 [!code-vb[VbVbcnProcedures #&58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 手順については、1 つ以上の省略可能なパラメーターでは、前の例と同様のロジックによってに到着した暗黙のオーバー ロードのセット。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>暗黙のオーバー ロード (paramarray の) パラメーター  
 コンパイラは、使用してプロシージャを[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーターを無限数のオーバー ロード、互いにどのような呼び出し元のコードに渡すパラメーターの配列、次のようにします。  
  
-   1 つのオーバー ロードを呼び出し元のコードでは引数に指定されていない場合、`ParamArray`  
  
-   1 つのオーバー ロードを呼び出し元のコードでの&1; 次元配列を提供する場合、`ParamArray`要素の型  
  
-   すべての正の整数のいずれかのオーバー ロードの呼び出し元のコードは、それぞれの引数をその数を指定すると、`ParamArray`要素の型  
  
 次の宣言では、これらの暗黙的なオーバー ロードを示しています。  
  
 [!code-vb[VbVbcnProcedures #&68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 パラメーター配列の&1; 次元配列を受け取り、パラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、その他の暗黙のオーバー ロードの署名を使用することができます。 次の宣言では、これを示しています。  
  
 [!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>オーバー ロードの代わりとしてを省略したプログラミング  
 パラメーターに異なるデータ型を渡すには、呼び出し元のコードを許可する場合、別の方法を省略したプログラミングします。 型チェックをスイッチを設定する`Off`いずれかで、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション。 パラメーターのデータ型を宣言する必要はありません。 ただし、このアプローチでは、オーバー ロードと比較して、次の欠点があります。  
  
-   省略したプログラミングでは、効率がよく実行コードを生成します。  
  
-   プロシージャは、渡されると予想されるすべてのデータ型をテストする必要があります。  
  
-   呼び出し元のコードが、プロシージャがサポートされていないデータ型を渡すかどうか、コンパイラでエラーが生成されません。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)   
 [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)   
 [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [オーバー ロードの解決](./overload-resolution.md)   
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
