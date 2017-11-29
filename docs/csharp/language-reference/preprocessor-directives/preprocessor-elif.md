---
title: "#<a name=\"elif-c-reference\"></a>elif (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#elif'
helpviewer_keywords: '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (C# リファレンス)
`#elif` を使用すると、複合条件付きディレクティブを作成できます。 `#elif` 式が評価されるのは、先行するディレクティブ式 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) および `#elif` (オプション) が `true` と評価されなかった場合です。 `#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。 例:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 複数のシンボルを評価するときには、`==` (等値)、`!=` (非等値)、`&&` (AND)、および `||` (OR) の演算子を使用できます。 シンボルと演算子は、かっこを使用してグループ化できます。  
  
## <a name="remarks"></a>コメント  
 `#elif` では、次のように記述した場合と同じ結果が得られます。  
  
```csharp
#else  
#if  
```  
  
 `#elif` を使用する方が簡単です。`#if` には対になる [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が必要ですが、`#elif` では対応する `#endif` が不要なためです。  
  
 `#elif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
