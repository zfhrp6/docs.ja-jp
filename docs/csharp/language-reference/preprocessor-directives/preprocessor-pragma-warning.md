---
title: "#pragma warning (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a>#pragma 警告 (C# リファレンス)
`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。  
  
## <a name="syntax"></a>構文  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a>パラメーター  
 `warning-list`  
 警告番号のコンマ区切りのリスト。 "CS" というプレフィックスは省略可能です。  
  
 警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。  
  
> [!NOTE]
>  Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。  
  
## <a name="example"></a>例  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [C# コンパイラ エラー](../../../csharp/language-reference/compiler-messages/index.md)
