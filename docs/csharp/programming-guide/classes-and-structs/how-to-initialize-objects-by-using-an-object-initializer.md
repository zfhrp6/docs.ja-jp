---
title: '方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 1f5f068cd8dc3787eb8cb2cd72cc30e9ea159390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド)
オブジェクト初期化子を使用すると、型のコンストラクターを明示的に呼び出さずに、宣言的な方法で型オブジェクトを初期化できます。  
  
 次の例は、指定したオブジェクトでオブジェクト初期化子を使用する方法を示しています。 コンパイラは、最初に既定のインスタンス コンストラクターにアクセスし、メンバーの初期化を処理することで、オブジェクト初期化子を処理します。 そのため、クラスで既定のコンストラクターが `private` として宣言されている場合、パブリック アクセスを必要とするオブジェクト初期化子は失敗します。  
  
 匿名型を定義する場合は、オブジェクト初期化子を使用する必要があります。 詳細については、「[方法: クエリで要素のプロパティのサブセットを返す](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、オブジェクト初期化子を使用して、新しい `StudentName` 型を初期化する方法を示しています。  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>例  
 次の例は、コレクション初期化子を使用して、`StudentName` 型のコレクションを初期化する方法を示しています。 コレクション初期化子は、コンマで区切られた一連のオブジェクト初期化子です。  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコードを実行するには、クラスをコピーし、Visual Studio で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
