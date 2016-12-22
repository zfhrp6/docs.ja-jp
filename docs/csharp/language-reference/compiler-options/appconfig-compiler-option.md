---
title: "/appconfig (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/appconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/appconfig compiler option [C#]"
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /appconfig (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/appconfig** コンパイラ オプションは、アセンブリのバインド時に、共通言語ランタイム \(CLR: Common Language Runtime\) に対して C\# アプリケーションがアセンブリのアプリケーション構成 \(app.config\) ファイルの場所を指定できるようにします。  
  
## 構文  
  
```  
/appconfig:file  
```  
  
## Arguments  
 `file`  
 必須。  アセンブリのバインド設定を含むアプリケーション構成ファイルです。  
  
## 解説  
 **\/appconfig** の 1 種類を使用すると、アセンブリが特定の参照アセンブリの Silverlight バージョンの .NET Framework version と .NET Framework の両方を同時に参照しなければならない高度なシナリオです。  たとえば、WPF \(Windows Presentation Foundation\) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップを参照すると共に、Silverlight に組み込まれている WPF のサブセットも参照することが必要な場合があります。  このデザイナー アセンブリは両方のアセンブリにアクセスする必要があります。  既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。  
  
 **\/appconfig** コンパイラ オプションを使用すると、`<supportPortability>` タグを使用して既定の動作を無効にする app.config ファイルの場所を指定できます。次に例を示します。  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 コンパイラは、ファイルの場所を CLR のアセンブリ バインディング ロジックに渡します。  
  
> [!NOTE]
>  Microsoft Build Engine \(MSBuild\) を使用してアプリケーションをビルドする場合は、プロパティ タグを .csproj ファイルに追加して **\/appconfig** コンパイラ オプションを設定できます。  プロジェクトで既に設定されている app.config ファイルを使用するには、プロパティ タグ `<UseAppConfigForCompiler>` を .csproj ファイルに追加し、その値を `true` に設定します。  別の app.config ファイルを指定するには、プロパティ タグ `<AppConfigForCompiler>` を追加し、その値をファイルの場所に設定します。  
  
## 使用例  
 次の例は、.NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリに対して、アプリケーションが .NET Framework の実装と .NET Framework for Silverlight の実装の両方を参照できるようにする app.config ファイルを示しています。  **\/appconfig** コンパイラ オプションは、この app.config ファイルの場所を指定します。  
  
```  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## 参照  
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/ja-jp/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)   
 [\<supportPortability\> 要素](../Topic/%3CsupportPortability%3E%20Element.md)   
 [C\# Compiler Options Listed Alphabetically](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)