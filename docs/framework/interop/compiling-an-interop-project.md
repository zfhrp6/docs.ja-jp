---
title: "相互運用プロジェクトのコンパイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, コンパイル"
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "コンパイル (相互運用プロジェクトの)"
  - "公開 (.NET Framework に COM コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), コンパイル"
  - "相互運用 (アンマネージ コードとの), 公開 (COM コンポーネントを)"
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 相互運用プロジェクトのコンパイル
インポートされた COM 型を格納した 1 つ以上のアセンブリを参照する COM 相互運用プロジェクトは、他のマネージ プロジェクトと同じ方法でコンパイルされます。  相互運用機能アセンブリは、Visual Studio などの開発環境で参照できます。または、コマンド ライン コンパイラを使用して参照できます。  どちらの場合でも、正常にコンパイルするには、相互運用機能アセンブリを、その他のプロジェクト ファイルと同じディレクトリに配置する必要があります。  
  
 相互運用機能アセンブリを参照する方法には、次の 2 つがあります。  
  
-   埋め込まれた相互運用機能型を使用する: [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] および [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。  この手法を使用することをお勧めします。  
  
-   相互運用機能アセンブリを配置する: 相互運用機能アセンブリへの標準の参照を作成できます。  この場合、アプリケーションで相互運用機能アセンブリを配置する必要があります。  
  
 この 2 つの方法の違いの詳細については、「[Using COM Types in Managed Code](http://msdn.microsoft.com/ja-jp/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)」を参照してください。  
  
 Visual Studio での相互運用機能型の埋め込みについては、「[チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」および「[チュートリアル: マネージ アセンブリからの型の埋め込み](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 コマンド ライン コンパイラを使用して相互運用機能アセンブリを参照し、実行可能ファイルに型情報を埋め込むには、[\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) コンパイラ スイッチまたは [\/link](../Topic/-link%20\(Visual%20Basic\).md) コンパイラ スイッチを使用し、相互運用機能アセンブリの名前を指定します。  
  
> [!NOTE]
>  Visual C\+\+ アプリケーションは型情報を埋め込むことはできませんが、型情報を埋め込むことができるアプリケーションまたはアドインと相互運用できます。  
  
 配置時にプライマリ相互運用機能アセンブリを含むアプリケーションをコンパイルするには、**\/reference** コンパイラ スイッチを使用し、相互運用機能アセンブリの名前を指定します。  
  
## 参照  
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)   
 [言語への非依存性、および言語非依存コンポーネント](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/ja-jp/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [チュートリアル: マネージ アセンブリからの型の埋め込み](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)