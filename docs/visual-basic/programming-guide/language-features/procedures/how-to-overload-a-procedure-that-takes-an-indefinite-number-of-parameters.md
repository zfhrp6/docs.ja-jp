---
title: '方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651493"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)
プロシージャがある場合、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、パラメーター配列の 1 次元配列を取得、オーバー ロードされたバージョンを定義することはできません。 詳細についてを参照してください「暗黙的なオーバー ロードを ParamArray パラメーター」[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>可変個のパラメーターを受け取るプロシージャをオーバー ロードするには  
  
1.  確認することは、プロシージャを呼び出すコード ロジック メリットがオーバー ロードされたバージョンから複数の`ParamArray`パラメーター。 「オーバー ロードと Paramarray」を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)です。  
  
2.  パラメーター リストの可変部分で、プロシージャが受け取る指定された値の数を決定します。 これは、値はありませんの大文字と小文字を含めることし、1 つの 1 次元配列の大文字と小文字を含めることがあります。  
  
3.  指定された値の許容数がそれぞれ、書き込み、`Sub`または`Function`対応するパラメーター リストを定義する宣言ステートメントです。 使用しないで、`Optional`または`ParamArray`このオーバー ロードされたバージョンではキーワードです。  
  
4.  各宣言の前に、`Sub`または`Function`キーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
5.  次の各宣言には、呼び出し元のコードは、その宣言のパラメーター リストに対応する値を指定した場合に実行するプロシージャ コードを記述します。  
  
6.  各プロシージャの終了、`End Sub`または`End Function`に応じてステートメントです。  
  
## <a name="example"></a>例  
 次の例で定義されている手順を示しています、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、および、同等の一連のオーバー ロードされたプロシージャです。  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 パラメーター配列の 1 次元配列を受け取るパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、他の暗黙的なオーバー ロードの署名を使用することができます。 次の宣言では、この問題を説明します。  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 オーバー ロードされたバージョンのコードは呼び出し元のコードの 1 つまたは複数の値を指定するかどうかをテストする必要はありません、`ParamArray`パラメーター、その場合、または数。 Visual Basic では、呼び出し元の引数リストに一致するバージョンに制御を渡します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 使用するプロシージャを`ParamArray`パラメーターは、一連のオーバー ロードされたバージョンに、これらの暗黙的なオーバー ロードのいずれかに対応するパラメーター リストで、このようなプロシージャをオーバー ロードできません。 詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。 パラメーター配列を受け取る場合は、呼び出し元のコードが渡された配列の長さのテストしはアプリケーションには大きすぎる場合は、適切な手順を実行する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [省略可能なパラメーター](./optional-parameters.md)  
 [パラメーター配列](./parameter-arrays.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)  
 [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)  
 [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [オーバーロードの解決](./overload-resolution.md)
