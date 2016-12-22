---
title: "方法: コマンド ライン引数を表示する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コマンド ライン引数 [C#], 表示"
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: コマンド ライン引数を表示する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

実行可能ファイルに対してコマンド ラインで指定した引数には、省略可能なパラメーターを介して `Main` からアクセスできます。  引数は、文字列の配列の形式で指定します。  配列の各要素には、1 つの引数が格納されます。  引数間の空白は削除されます。  架空の実行可能ファイルを呼び出すためのコマンド ラインの例を次に示します。  
  
|コマンド ラインでの入力|Main に渡される文字列の配列|  
|------------------|----------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
>  Visual Studio でアプリケーションを実行する場合、「[\[デバッグ\] ページ \(プロジェクト デザイナー\)](../Topic/Debug%20Page,%20Project%20Designer.md)」のコマンド ライン引数を指定できます。  
  
## 使用例  
 この例は、コマンド ライン アプリケーションに渡されるコマンド ライン引数を示しています。  次の出力は、上の表の最初のエントリに対するものです。  
  
 [!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Main\(\) とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main\(\) の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)