---
title: "方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>方法 : ポインターを使用してバイトの配列をコピーする (C# プログラミング ガイド)
次の例では、ポインターを使って 1 つの配列から別の配列にバイトをコピーします。  
  
 この例では、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使います。このキーワードは、`Copy` メソッドでのポインターの使用を可能にします。 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) ステートメントを使って、コピー元とコピー先の配列へのポインターを宣言します。 これにより、コピー元配列とコピー先配列のメモリ内での位置を "*固定*" し、ガベージ コレクションによって移動されないようにします。 `fixed` ブロックが完了すると、これらの配列のメモリ ブロックは固定解除されます。 この例の `Copy` メソッドは `unsafe` キーワードを使っているので、**/unsafe** コンパイラ オプションを指定してコンパイルする必要があります。 Visual Studio でオプションを設定するには、プロジェクト名を右クリックして、**[プロパティ]** をクリックします。 **[ビルド]** タブで **[アンセーフ コードの許可]** を選択します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/unsafe (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [ガベージ コレクション](../../../standard/garbage-collection/index.md)
