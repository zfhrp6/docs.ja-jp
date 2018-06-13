---
title: '方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 1da1d67726a9669477721aabc0aace0119aa7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652897"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)
プロシージャが 1 つまたは複数場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーター、暗黙的なオーバー ロードのいずれかに一致するオーバー ロード バージョンを定義することはできません。 詳細についてを参照してください"暗黙的なオーバー ロードの省略可能なパラメーター"[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。  
  
## <a name="one-optional-parameter"></a>1 つの省略可能なパラメーター  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>1 つの省略可能なパラメーターを受け取るプロシージャをオーバー ロード  
  
1.  書き込み、`Sub`または`Function`パラメーター リストで省略可能なパラメーターを含む宣言ステートメントです。 使用しないで、`Optional`このオーバー ロードされたバージョンではキーワードです。  
  
2.  前に、`Sub`または`Function`キーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
3.  呼び出し元のコードには、省略可能な引数が指定されている場合に実行するプロシージャ コードを記述します。  
  
4.  使用してプロシージャを終了、`End Sub`または`End Function`に応じてステートメントです。  
  
5.  パラメーター リストで省略可能なパラメーターを含まないする点を除いて、最初の宣言と同じである 2 つ目の宣言ステートメントを記述します。  
  
6.  呼び出し元のコードは、省略可能な引数を指定していない場合に実行するプロシージャ コードを記述します。 使用してプロシージャを終了、`End Sub`または`End Function`に応じてステートメントです。  
  
     次の例では、2 つのオーバー ロードされたプロシージャでは、そして最後に無効なと無効の両方のオーバー ロードされたバージョンの省略可能なパラメーターを指定して定義された手順を示します。  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>複数の省略可能なパラメーター  
 省略可能なパラメーターを 1 つ以上の手順は、通常 2 つ以上のオーバー ロードされたバージョンを必要です。 たとえば、2 つの省略可能なパラメーターがあると、呼び出し元のコードを指定したり省略とは無関係に、他の 1 つずつ、4 つのオーバー ロードされたバージョンを組み合わせて指定された引数のいずれか必要があります。  
  
 省略可能なパラメーターの数が多いほど、オーバー ロードの複雑さが増加します。 指定された引数のいくつかの組み合わせが許されない限り、N の省略可能なパラメーターにする必要があります 2 ^ N のオーバー ロードされたバージョンです。 プロシージャの性質、によって、わかりやすくするためのロジックが妥当な労力をすべてのオーバー ロードされたバージョンを定義することがあります。  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>1 つ以上の省略可能なパラメーターを受け取るプロシージャをオーバー ロード  
  
1.  プロシージャのロジックを受け入れ可能な省略可能な引数の組み合わせが判断します。 無効な組み合わせは、別の 1 つの省略可能なパラメーターが依存している場合に発生する可能性です。 たとえば、1 つのパラメーターは、配偶者の名前を受け入れ、配偶者の年齢を受け取る場合は、経過期間を指定することが、名前を省略する引数の組み合わせは使用できません。  
  
2.  省略可能な引数の許容可能な組み合わせごとに、書き込み、`Sub`または`Function`対応するパラメーター リストを定義する宣言ステートメントです。 使用しないで、`Optional`キーワード。  
  
3.  各宣言の前に、`Sub`または`Function`キーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
4.  次の各宣言には、呼び出し元のコードは、その宣言のパラメーター リストに対応する引数リストを指定した場合に実行するプロシージャ コードを記述します。  
  
5.  各プロシージャの終了、`End Sub`または`End Function`に応じてステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [省略可能なパラメーター](./optional-parameters.md)  
 [パラメーター配列](./parameter-arrays.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)  
 [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)  
 [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [オーバーロードの解決](./overload-resolution.md)
