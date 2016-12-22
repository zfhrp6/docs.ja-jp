---
title: "How to: Set Environment Variables for the Visual Studio Command Line | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.build.commandline"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "csc.exe, command-line builds"
  - "Visual C#, command-line builds"
  - "command-line compilers, Visual C#"
  - "Vsvars32.bat"
  - "builds [C#], command-line"
  - "compilers, invoking from command line"
  - "Vcvars32.bat file"
  - "command line [C#], building from"
  - "Visual C# compiler, enabling"
  - "compiling source code, from command line"
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Set Environment Variables for the Visual Studio Command Line
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

vcvars32.bat ファイルは、適切な環境変数を設定してコマンド ライン ビルドを有効にします。  vsvars32.bat の詳細については、[サポート技術情報の記事 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042) を参照してください。  
  
 以前のバージョンの Visual Studio と最新バージョンの Visual Studio の両方がコンピューターにインストールされている場合は、同じコマンド プロンプト ウィンドウから異なるバージョンの vsvars32.bat または vcvars32.bat を実行しないでください。  
  
### VSVARS32.BAT を実行するには  
  
1.  **\[スタート\]** メニューから、**VS2012 の開発者コマンド プロンプト**を開きます。  
  
2.  インストールの Program Files\\Microsoft Visual Studio *Version*\\Common7\\Tools または Program Files \(x86\)\\Microsoft Visual Studio *Version*\\Common7\\Tools サブディレクトリに移動します。  
  
3.  「VSVARS32」と入力して VSVARS32.bat を実行します。  
  
    > [!CAUTION]
    >  VSVARS32.bat の場所は、コンピューターによって異なる場合があります。  VSVARS32.bat ファイルが見つからない場合や破損している場合でも、別のコンピューターの VSVARS32.bat と置き換えないでください。  その場合は、セットアップ プログラムを再実行してファイルを置き換えてください。  
  
## 参照  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)