---
title: "型引数をデリゲートから推論できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords: BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>型引数をデリゲートから推論できませんでした
代入ステートメントは、 `AddressOf` を使用してジェネリック プロシージャのアドレスをデリゲートに割り当てますが、ジェネリック プロシージャに型引数を指定していません。  
  
 通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推論しようとします。 コンテキストにコンパイラが型を推論するのに十分な情報が提供されていない場合は、エラーが生成されます。  
  
 **エラー ID:** BC36564  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ジェネリック プロシージャの型引数を `AddressOf` 式で指定します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Visual Basic におけるジェネリック プロシージャ](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)  
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
