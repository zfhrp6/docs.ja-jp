---
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a>DLL を正しく呼び出せません。
ダイナミック リンク ライブラリ (DLL) に渡された引数が、ルーチンによって予測されるを正確に一致する必要があります。 呼び出し規約は、サーバーの数、種類、および引数の順序を使用します。 プログラムが間違った型または引数の数が渡される DLL にルーチンを呼び出している可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  すべての引数の型が呼び出しには、ルーチンの宣言で指定されている条項に同意することを確認します。  
  
2.  同じ数の呼び出しには、ルーチンの宣言に示されている引数を渡していることを確認してください。  
  
3.  DLL 内のルーチンは、値によって引数が必要ですが場合、確認`ByVal`ルーチンの宣言でこれらの引数が指定されています。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
