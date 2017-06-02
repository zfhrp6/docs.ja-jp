---
title: "方法 : DEVPATH を使用してアセンブリを指定する | Microsoft Docs"
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
  - ".NET Framework アプリケーション構成, アセンブリ"
  - "app.config ファイル, アセンブリの場所"
  - "アプリケーション構成ファイル, 指定 (アセンブリの場所を)"
  - "アセンブリ [.NET Framework], 位置"
  - "DEVPATH"
  - "検索 (アセンブリを)"
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 方法 : DEVPATH を使用してアセンブリを指定する
開発者は、作成する共有アセンブリが複数のアプリケーションで正しく動作することを確認する必要があります。  開発時に、グローバル アセンブリ キャッシュにアセンブリを繰り返し配置する代わりに、アセンブリのビルド出力ディレクトリを指す DEVPATH 環境変数を作成できます。  
  
 たとえば、MySharedAssembly という共有アセンブリを作成していて、その出力ディレクトリが C:\\MySharedAssembly\\Debug であると仮定します。  開発者は、C:\\MySharedAssembly\\Debug を DEVPATH 変数に格納できます。  マシン構成ファイル内に [\<developmentMode\>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) 要素を指定する必要があります。  この要素は、共通言語ランタイムに、DEVPATH を使用してアセンブリを特定するように指示します。  
  
 共有アセンブリは、実行時に検出可能にする必要があります。アセンブリ参照を解決するためのプライベート ディレクトリを指定するには、「[アセンブリの場所の指定](../../../docs/framework/configure-apps/specify-assembly-location.md)」で説明されているように、構成ファイルで [\<codeBase\> 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) または [\<probing\> 要素](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) を使用します。アセンブリをアプリケーション ディレクトリのサブディレクトリに入れることもできます。  詳細については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
> [!NOTE]
>  これは、開発者専用の高度な機能です。  
  
 DEVPATH 環境変数で指定されたディレクトリでランタイムがアセンブリを検索するように指定する例を示します。  
  
## 使用例  
  
```  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 この設定の既定値は、false です。  
  
> [!NOTE]
>  この設定は、開発時にだけ使用します。  ランタイムは、DEVPATH で見つかった厳密な名前付きアセンブリのバージョンを確認しません。  単純に、最初に見つかったアセンブリを使用します。  
  
## 参照  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/ja-jp/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)