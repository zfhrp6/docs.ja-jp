---
title: "/target (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/target"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#]"
  - "/target compiler options [C#]"
  - "assemblies [C#], compiling"
  - "-target compiler options [C#]"
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# /target (C# Compiler Options)
**\/target** コンパイラ オプションを指定するには、次の 4 つの形式のいずれかを使用します。  
  
 [\/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)] アプリケーションの .exe ファイルを作成する場合。  
  
 [\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 .exe ファイルを作成する場合。  
  
 [\/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 コード ライブラリを作成する場合。  
  
 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 モジュールを作成する場合。  
  
 [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Windows プログラムを作成する場合。  
  
 [\/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 中間 .winmdobj ファイルが作成されます。  
  
 **\/target:module** を指定しない限り、**\/target** を使用すると、.NET Framework のアセンブリ マニフェストが出力ファイルに組み込まれます。  詳細については、「[共通言語ランタイムのアセンブリ](../Topic/Assemblies%20in%20the%20Common%20Language%20Runtime.md)」および「[共通の属性](../Topic/Common%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 アセンブリ マニフェストは、コンパイル中の最初の .exe 出力ファイルに組み込まれます。.exe 出力ファイルがない場合には、最初の DLL ファイルに組み込まれます。  たとえば、次のコマンド ラインでは、マニフェストは `1.exe` に組み込まれます。  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 コンパイラの 1 回のコンパイルで作成されるアセンブリ マニフェストは 1 つだけです。  コンパイルにおけるすべてのファイルの情報は、アセンブリ マニフェストに含まれます。  **\/target:module** 以外で作成されたすべての出力ファイルは、アセンブリ マニフェストを含むことができます。  コマンド ラインで複数の出力ファイルを生成するときは、アセンブリ マニフェストが 1 つだけ作成されます。このアセンブリ マニフェストは、コマンド ラインで指定した最初の出力ファイルに含める必要があります。  最初の出力ファイル \(**\/target:exe**、**\/target:winexe**、**\/target:library**、または **\/target:module**\) にかかわらず、同じコンパイル処理で作成する他の出力ファイルはモジュール \(**\/target:module**\) にする必要があります。  
  
 アセンブリを作成する場合は、<xref:System.CLSCompliantAttribute> 属性を使用して、コードのすべてまたは一部が CLS 準拠であることを指定できます。  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 このコンパイラ オプションをプログラムで設定する方法の詳細については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [\/subsystemversion \(Specify minimum subsystem version\)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)