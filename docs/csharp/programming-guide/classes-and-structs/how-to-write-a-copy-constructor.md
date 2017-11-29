---
title: "方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>方法 : コピー コンストラクターを記述する (C# プログラミング ガイド)
C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。  
  
## <a name="example"></a>例  
 次の例の `Person` [クラス](../../../csharp/language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。 引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。 このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ICloneable>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)
