---
title: 静的コンストラクター (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 52c52f68bc3612807b810047044aedbd2c457cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315712"
---
# <a name="static-constructors-c-programming-guide"></a>静的コンストラクター (C# プログラミング ガイド)
静的コンストラクターは、任意の [static](../../../csharp/language-reference/keywords/static.md) データを初期化するため、または 1 回だけ実行する必要がある特定のアクションを実行するために使います。 最初のインスタンスが作成され前、または静的メンバーが参照される前に、自動的に呼び出されます。  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 静的コンストラクターには、次の特徴があります。  
  
-   静的コンストラクターはアクセス修飾子を取らず、パラメーターはありません。  
  
-   静的コンストラクターは、最初のインスタンスが作成され前、または静的メンバーが参照される前に、[クラス](../../../csharp/language-reference/keywords/class.md)を初期化するために自動的に呼び出されます。  
  
-   静的コンストラクターを直接呼び出すことはできません。  
  
-   ユーザーは、プログラムで静的コンストラクターが実行されるタイミングを制御できません。  
  
-   静的コンストラクターの一般的な用途は、クラスがログ ファイルを使っていて、このファイルにエントリを書き込むためにコンストラクターが使われる場合です。  
  
-   コンストラクターが `LoadLibrary` メソッドを呼び出すことができる場合は、アンマネージ コードのラッパー クラスを作成するときにも静的コンストラクターが役に立ちます。  
  
-   静的コンストラクターが例外をスローした場合、ランタイムがその静的コンストラクターを再度呼び出すことはなく、その型は、プログラムが実行しているアプリケーション ドメインの有効期間中、初期化されないままになります。  
  
## <a name="example"></a>例  
 この例では、`Bus` クラスに静的コンストラクターがあります。 `Bus` の最初のインスタンスが作成されるとき (`bus1`)、静的コンストラクターが呼び出されてクラスが初期化されます。 サンプルの出力では、`Bus` のインスタンスが 2 つでも静的コンストラクターは 1 回だけ実行されること、およびインスタンス コンストラクターの実行前に静的コンストラクターが実行されることがわかります。  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)
