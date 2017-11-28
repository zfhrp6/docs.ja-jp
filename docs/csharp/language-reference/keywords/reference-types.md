---
title: "参照型 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a>参照型 (C# リファレンス)
C# では、参照型と値型という 2 種類の型をサポートしています。 参照型の変数はデータ (オブジェクト) への参照を格納するのに対して、値型の変数はデータを直接格納します。 参照型の場合、2 つの変数が同じオブジェクトを参照できるため、ある変数に対する演算によって、他の変数が参照しているオブジェクトが影響を受ける可能性があります。 値型の場合、各変数が独自のデータ コピーを保持し、ある変数に対する操作が別の変数に影響を与えることはありません (ref パラメーターと out パラメーターの変数を除きます。「[ref](../../../csharp/language-reference/keywords/ref.md)」と「[out パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md)」を参照してください)。  
  
 次のキーワードは、参照型を宣言するときに使用します。  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 C# では次の組み込みの参照型も使用できます。  
  
-   [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [object](../../../csharp/language-reference/keywords/object.md)  
  
-   [string](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)
