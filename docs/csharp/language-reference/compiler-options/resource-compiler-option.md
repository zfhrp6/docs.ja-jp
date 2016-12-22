---
title: "/resource (C# Compiler Options) | Microsoft Docs"
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
  - "/resource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-resource compiler option [C#]"
  - "/resource compiler option [C#]"
  - "-res compiler option [C#]"
  - "/res compiler option [C#]"
  - "res compiler option [C#]"
  - "resource compiler option [C#]"
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /resource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定されたリソースを出力ファイルに埋め込みます。  
  
## 構文  
  
```  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 出力ファイルに埋め込む .NET Framework リソース ファイル。  
  
 `identifier` \(省略可能\)  
 リソースの論理名。リソースの読み込みに使用します。  既定値はファイルの名前です。  
  
 `accessibility-modifier` \(省略可能\)  
 リソースのアクセシビリティ \(public または private\)。  既定値は public です。  
  
## 解説  
 [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) を使用すると、リソースがアセンブリにリンクされ、リソース ファイルは出力ファイルに追加されません。  
  
 既定では、C\# コンパイラを使用して作成したリソースは、アセンブリ内で public になります。  リソースを private にする場合は、`private` をアクセシビリティ修飾子として指定します。  `public` と `private` 以外のアクセシビリティは使用できません。  
  
 `filename` が .NET Framework リソース ファイルである場合、たとえば [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) や開発環境で作成されたものである場合は、<xref:System.Resources> 名前空間のメンバーを使用してアクセスできます。  詳細については、「<xref:System.Resources.ResourceManager?displayProperty=fullName>」を参照してください。  それ以外のすべてのリソースに対しては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource`\* メソッドを使用して、実行時にリソースにアクセスします。  
  
 **\/res** は **\/resource** の省略形です。  
  
 出力ファイルにおけるリソースの順序は、コマンド ラインでの指定順序に基づいて決定されます。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトにリソース ファイルを追加します。  
  
2.  **ソリューション エクスプローラー**で、埋め込むファイルを選択します。  
  
3.  選択したファイルの **\[プロパティ\]** ウィンドウで、**\[ビルド アクション\]** をクリックします。  
  
4.  **\[ビルド アクション\]** を **\[埋め込まれたリソース\]** に設定します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.FileProperties2.BuildAction%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、リソース ファイル `rf.resource` をアタッチする例を次に示します。  
  
```  
csc /resource:rf.resource in.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)