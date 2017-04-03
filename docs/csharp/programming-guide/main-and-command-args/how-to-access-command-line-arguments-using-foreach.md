---
title: "方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2f0e3bce88beafd45a21773a7b26ffb2bb41215d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)
配列の反復処理には、この例で示すように [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用する方法もあります。 `foreach` ステートメントは、配列、.NET Framework コレクション クラス、または <xref:System.Collections.IEnumerable> インターフェイスを実装する任意のクラスや構造体の反復処理に使用できます。  
  
> [!NOTE]
>  Visual Studio でアプリケーションを実行する場合、「[[デバッグ] ページ (プロジェクト デザイナー)](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer)」のコマンド ライン引数を指定できます。  
  
## <a name="example"></a>例  
 この例では、`foreach` を使用したコマンド ライン引数の出力方法を示します。  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Array>   
 <xref:System.Collections>   
 [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
