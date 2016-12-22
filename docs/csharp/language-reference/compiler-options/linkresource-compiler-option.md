---
title: "/linkresource (C# Compiler Options) | Microsoft Docs"
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
  - "/linkresource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/linkresource compiler option [C#]"
  - "linkres compiler option [C#]"
  - "/linkres compiler option [C#]"
  - "-linkres compiler option [C#]"
  - "-linkresource compiler option [C#]"
  - "linkresource compiler option [C#]"
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /linkresource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

.NET Framework リソースへのリンクを出力ファイルに作成します。  リソース ファイルは出力ファイルには追加されません。  これは、リソース ファイルを出力ファイルに埋め込む [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) オプションとは異なります。  
  
## 構文  
  
```  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 アセンブリからのリンク先である .NET Framework リソース ファイル。  
  
 `identifier` \(省略可能\)  
 リソースの論理名。リソースの読み込みに使用します。  既定値はファイル名です。  
  
 `accessibility-modifier` \(省略可能\)  
 リソースのアクセシビリティ \(public または private\)。  既定値は public です。  
  
## 解説  
 既定では、リンクされたリソースを C\# コンパイラで作成すると、そのリソースはアセンブリ内で public になります。  リソースを private にする場合は、`private` をアクセシビリティ修飾子として指定します。  `public` と `private` 以外の修飾子は使用できません。  
  
 **\/linkresource** では、**\/target:module** 以外のいずれかの [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションが必要です。  
  
 `filename` が .NET Framework リソース ファイルである場合、たとえば [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) や開発環境で作成されたものである場合は、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます。  詳細については、「<xref:System.Resources.ResourceManager?displayProperty=fullName>」を参照してください。  それ以外のすべてのリソースに対しては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource`\* メソッドを使用して、実行時にリソースにアクセスします。  
  
 `filename` に指定するファイルの形式は任意です。  たとえば、ネイティブ DLL をアセンブリの一部として含め、そのネイティブ DLL をグローバル アセンブリ キャッシュにインストールして、アセンブリ内のマネージ コードからアクセスできるようにすることもできます。  以下の 2 つ目の例では、この方法が示されています。  これと同じことは、アセンブリ リンカーで行うこともできます。  以下の 3 つ目の例では、この方法が示されています。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」および「[アセンブリとグローバル アセンブリ キャッシュの使用](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)」を参照してください。  
  
 **\/linkres** は **\/linkresource** の省略形です。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
## 使用例  
 `in.cs` をコンパイルし、リソース ファイル `rf.resource` にリンクさせる例を次に示します。  
  
```  
csc /linkresource:rf.resource in.cs  
```  
  
## 使用例  
 `A.cs` をコンパイルして DLL を作成し、ネイティブの DLL N.dll にリンクして、出力をグローバル アセンブリ キャッシュ \(GAC\) に格納します。  次の例では、A.dll および N.dll の両方が GAC に格納されます。  
  
```  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## 使用例  
 次の例では、前の例と同じことをアセンブリ リンカーのオプションを使って実行します。  
  
```  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [アセンブリとグローバル アセンブリ キャッシュの使用](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)