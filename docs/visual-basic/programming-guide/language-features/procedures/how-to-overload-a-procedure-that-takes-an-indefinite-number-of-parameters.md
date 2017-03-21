---
title: "方法: 不特定数のパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロード |Microsoft ドキュメント"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: c7e09bd482e35c7ce7f28a6cc7de0379b7cc89f6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)
プロシージャがある場合、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、パラメーター配列の&1; 次元配列を取得するオーバー ロードされたバージョンを定義することはできません。 詳細については、「暗黙的なオーバー ロードに、ParamArray パラメーター」を参照してください[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>可変個のパラメーターを受け取るプロシージャをオーバー ロードするには  
  
1.  プロシージャは、コードのロジックとメリットを呼び出すことがから複数のバージョンのオーバー ロードされたことを確認、`ParamArray`パラメーター。 「オーバー ロードと Paramarray」を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。  
  
2.  パラメーター リストの可変部分で、プロシージャが受け取る指定された値の数を決定します。 値がない場合が挙げられ、1 つの&1; 次元配列の大文字と小文字を含めることがあります。  
  
3.  指定された値の許容数ごとに、書き込み、`Sub`または`Function`対応するパラメーター リストを定義する宣言ステートメントです。 使用しないで、`Optional`または`ParamArray`このオーバー ロードされたバージョンのキーワードです。  
  
4.  各宣言の前に、`Sub`または`Function`キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードです。  
  
5.  次の各宣言には、呼び出し元のコードには、その宣言のパラメーター リストに対応する値が指定されている場合に実行するプロシージャ コードを記述します。  
  
6.  各プロシージャの終了、`End Sub`または`End Function`に応じてステートメントです。  
  
## <a name="example"></a>例  
 次の例で定義された手順を示しています、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、および、同等の一連のオーバー ロードされたプロシージャ。  
  
 [!code-vb[VbVbcnProcedures #&69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 パラメーター配列の&1; 次元配列を受け取り、パラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、その他の暗黙のオーバー ロードの署名を使用することができます。 次の宣言では、これを示しています。  
  
 [!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 オーバー ロードされたバージョンのコードは呼び出し元のコードの&1; つまたは複数の値を指定するかどうかをテストする必要はありません、`ParamArray`パラメーター、その場合、または数。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出しの引数リストに一致するバージョンに制御を渡す。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 の手順、`ParamArray`パラメーターは、一連のオーバー ロードされたバージョンに、これらの暗黙的なオーバー ロードのいずれかに対応する、パラメーター リストでこのようなプロシージャをオーバー ロードすることはできません。 詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 無制限に大きくなる可能性の配列を処理するたびに、アプリケーションの内部の容量を超過してしまう可能性があります。 パラメーターの配列を受け取る場合に、呼び出し元のコードが渡された配列の長さをテストし、アプリケーションに対して大きすぎる場合は、適切な手順を実行します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [省略可能なパラメーター](./optional-parameters.md)   
 [パラメーター配列](./parameter-arrays.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)   
 [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)   
 [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [オーバーロードの解決](./overload-resolution.md)
