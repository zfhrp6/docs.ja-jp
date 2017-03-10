---
title: "/debug (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/debug"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "debug compiler option [C#]"
  - "-debug compiler option [C#]"
  - "/debug compiler option [C#]"
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# /debug (C# Compiler Options)
**\/debug** オプションを指定すると、コンパイラによってデバッグ情報が生成され、出力ファイルに格納されます。  
  
## 構文  
  
```  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## Arguments  
 `+` &#124; `-`  
 `+` を指定するか、または単に **\/debug** と指定すると、コンパイラによってデバッグ情報が生成され、その情報がプログラム データベース \(.pdb ファイル\) に出力されます。  `-` を指定すると、デバッグ情報は作成されません。**\/debug** を指定しない場合は、\- と同じ結果になります。  
  
 `full` &#124; `pdbonly`  
 コンパイラによって生成されるデバッグ情報の種類を指定します。  **\/debug:pdbonly** を指定しない場合、つまり full 引数を使用すると、実行中のプログラムにデバッガーをアタッチできます。  pdbonly を指定すると、プログラムがデバッガーで開始されたときにはソース コードをデバッグできますが、実行中のプログラムをデバッガーにアタッチしたときはアセンブラーしか表示されません。  
  
## 解説  
 このオプションを使用してデバッグ ビルドを作成します。  **\/debug**、**\/debug\+**、**\/debug:full** のいずれも指定しなかった場合、プログラムの出力ファイルをデバッグすることはできません。  
  
 **\/debug:full** を使用する場合は、JIT によって最適化されるコードの速度とサイズに若干影響が生じる点に注意してください。また、**\/debug:full** でデバッグした場合、わずかではありますが、コードの品質にも影響が生じます。  リリース バージョンのコードには、**\/debug:pdbonly** を使用するか、PDB を一切使用しないことをお勧めします。  
  
> [!NOTE]
>  **\/debug:pdbonly** と **\/debug:full** の唯一の違いは、**\/debug:full** でコンパイルした場合、デバッグ情報が利用可能であることを JIT コンパイラに通知するための <xref:System.Diagnostics.DebuggableAttribute> が生成される点です。  したがって、**\/debug:full** を使用する場合に、コード内で <xref:System.Diagnostics.DebuggableAttribute> が false に設定されていると、エラーが生成されます。  
  
 アプリケーションのデバッグ パフォーマンスを構成する方法の詳細については、「[イメージのデバッグの簡略化](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)」を参照してください。  
  
 .pdb ファイルの場所を変更する方法については、「[\/pdb \(Specify Debug Symbol File\)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[デバッグ情報\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>」を参照してください。  
  
## 使用例  
 デバッグ情報をファイル `app.pdb` に出力する例を次に示します。  
  
```  
csc /debug /pdb:app.pdb test.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)