---
title: プロシージャのオーバーロードに関する注意事項 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: e1768d0ac03cb6730c4337d7476ae163e75adfd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654331"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>プロシージャのオーバーロードに関する注意事項 (Visual Basic)
プロシージャをオーバー ロードするときに使用する必要あります別*署名*オーバー ロードされたバージョンごとにします。 通常、このエラーは、各バージョンは、異なるパラメーター リストを指定する必要があることを意味します。 詳細についてを参照してください「異なる署名」[プロシージャのオーバー ロード](./procedure-overloading.md)です。  
  
 オーバー ロードすることができます、`Function`プロシージャを`Sub`プロシージャをその逆の場合は、異なる署名があるを提供します。 2 つのオーバー ロードできませんとは異なり、のみ戻り値を持つ 1 つともう一方にないです。  
  
 プロシージャのオーバー ロードするのと同様にプロパティをオーバー ロードできますと同じ制限事項があります。 ただし、プロシージャをオーバー ロードすることはできません、プロパティ、またはその逆です。  
  
## <a name="alternatives-to-overloaded-versions"></a>オーバー ロードされたバージョンに代わる方法  
 引数の有無は省略可能またはその数が可変である場合に特にオーバー ロードされたバージョンは、選択肢場合もありますがあります。  
  
 省略可能な引数が必ずしもすべての言語でサポートされていません、パラメーター配列は、Visual Basic に制限に注意してください。 任意のいくつかの異なる言語で記述されたコードから呼び出される可能性のあるプロシージャを作成している場合に、バージョンによって柔軟性がオーバー ロードされます。  
  
### <a name="overloads-and-optional-arguments"></a>省略可能な引数とオーバー ロード  
 呼び出し元のコードの指定または 1 つまたは複数の引数を省略できます必要に応じて、ときに、複数のオーバー ロードされたバージョンを定義または省略可能なパラメーターを使用できます。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義するを考慮することができます。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードに省略可能な引数が指定されていない、またはかどうかによって大きく異なります。  
  
-   プロシージャのコードは、呼び出し元のコードには、省略可能な引数が指定されているかどうかを確実にテストできません。 これは、ようななどの既定値の値を可能性のある候補がない場合は呼び出し元のコードいないと考えられるを指定します。  
  
#### <a name="when-to-use-optional-parameters"></a>省略可能なパラメーターを使用する場合  
 次の場合、1 つまたは複数の省略可能なパラメーターを好む場合があります。  
  
-   呼び出し元のコードは省略可能な引数を指定しない場合にのみ必要な操作では、既定値にパラメーターを設定します。 このような場合は、プロシージャのコードを単純化できますと 1 つ以上の 1 つのバージョンを定義する場合`Optional`パラメーター。  
  
 詳細については、次を参照してください。[省略可能なパラメーター](./optional-parameters.md)です。  
  
### <a name="overloads-and-paramarrays"></a>Paramarray とオーバー ロード  
 呼び出し元のコードは、可変個の引数を渡すことができます、ときに複数のオーバー ロードされたバージョンを定義したり、パラメーター配列を使用できます。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義するを考慮することができます。  
  
-   呼び出し元のコードことはありませんが合格する少数の値を超えるパラメーター配列にわかります。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードに渡す値の数によって大きく異なります。  
  
-   呼び出し元のコードは、異なるデータ型の値を渡すことができます。  
  
#### <a name="when-to-use-a-parameter-array"></a>パラメーター配列を使用する場合  
 方が、`ParamArray`パラメーターは、次の場合。  
  
-   呼び出し元のコードは、パラメーター配列を渡すことができます数の値を予測できないし、数が多い可能性があります。  
  
-   プロシージャのロジックは、呼び出し元のコードを渡します、すべての値に同じ操作を実行するすべての値を反復処理に適しています。  
  
 詳細については、次を参照してください。[パラメーター配列](./parameter-arrays.md)です。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>省略可能なパラメーターの暗黙のオーバー ロード  
 使用するプロシージャを[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメータは、省略可能なパラメーターを使用して 1 つと 2 つのオーバー ロードされたプロシージャに相当します。 これらのいずれかに対応するパラメーター リストで、このようなプロシージャをオーバー ロードできません。 次の宣言では、この問題を説明します。  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 省略可能なパラメーターを 1 つ以上の手順は、前の例と同様のロジックによって到着暗黙のオーバー ロードの集合であります。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray パラメーターの暗黙のオーバー ロード  
 コンパイラは、使用するプロシージャを[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)無数のオーバー ロードが互いにどのような呼び出し元のコードを渡しますはパラメーター配列に次のように異なるパラメーター。  
  
-   1 つのオーバー ロードの呼び出し元のコードでは引数に指定されていない場合、 `ParamArray`  
  
-   1 つのオーバー ロードの 1 次元配列を呼び出し元のコードが提供する場合の`ParamArray`要素の型  
  
-   すべての正の整数のいずれかのオーバー ロードの呼び出し元のコードは、それぞれの引数の数を指定した場合、`ParamArray`要素の型  
  
 次の宣言では、これらの暗黙的なオーバー ロードを示しています。  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 パラメーター配列の 1 次元配列を受け取るパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、他の暗黙的なオーバー ロードの署名を使用することができます。 次の宣言では、この問題を説明します。  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>オーバー ロードの代わりとしてを省略したプログラミング  
 パラメーターに異なるデータ型を渡すには、呼び出し元のコードを許可する場合は、別の方法を省略したプログラミングします。 型チェックにスイッチを設定することができます`Off`いずれかで、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション。 パラメーターのデータ型を宣言する必要はありません。 ただし、このアプローチでは、オーバー ロードと比較して次の欠点があります。  
  
-   省略したプログラミングでは、小さく効率的な実行コードを生成します。  
  
-   プロシージャに渡される可能性がすべてのデータ型をテストする必要があります。  
  
-   呼び出し元のコードが、プロシージャがサポートしていないデータ型を渡すかどうか、コンパイラでエラーが生成されません。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)  
 [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)  
 [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [オーバーロードの解決](./overload-resolution.md)  
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
