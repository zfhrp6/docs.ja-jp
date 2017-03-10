---
title: "/target:winmdobj (C# コンパイラ オプション) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /target:winmdobj (C# コンパイラ オプション)
**\/target:winmdobj** コンパイラ オプションを使用すると、コンパイラは、Windows ランタイム バイナリ ファイル \(.winmd\) に変換できる .winmdobj 中間ファイルを作成します。  .winmd ファイルは、マネージ言語プログラムだけでなく JavaScript および C\+\+ プログラムでも使用できます。  
  
## 構文  
  
```  
/target:winmdobj  
```  
  
## 解説  
 **winmdobj** 設定は、中間モジュールが必要であることをコンパイラに通知します。  これに対し、Visual Studio が C\# クラス ライブラリを .winmdobj ファイルとしてコンパイルします。  .winmdobj ファイルは <xref:Microsoft.Build.Tasks.WinMDExp> エクスポート ツールで送信され、Windows メタデータ ファイル \(.winmd\) が生成されます。  .winmd ファイルには、元のライブラリのコードと WinMD メタデータの両方が含まれています。メタデータは、JavaScript または C\+\+、および Windows ランタイムで使用されます。  
  
 **\/target:winmdobj** コンパイラ オプションを使用してコンパイルされたファイルの出力は、WimMDExp エクスポート ツール用の入力としてのみ使用するように設計されています。.winmdobj ファイル自体は直接参照されません。  
  
 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを使用しない限り、出力ファイル名は最初の入力ファイルと同じになります。  [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドは必要ではありません。  
  
 コマンド プロンプトで \/target:winmdobj オプションを指定すると、次の **\/out** または [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムを作成するために使用されます。  
  
### Windows ストア アプリ用に Visual Studio IDE でこのコンパイラ オプションを設定するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**\[プロパティ\]** をクリックします。  
  
2.  **\[アプリケーション\]** タブをクリックします。  
  
3.  **\[出力の種類\]** ボックスの一覧で、**\[WinMD ファイル\]** をクリックします。  
  
     **\[WinMD ファイル\]** オプションは、[!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)] アプリケーション テンプレートでのみ使用できます。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 次のコマンドは .winmdobj 中間ファイルに `filename.cs` をコンパイルします。  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)