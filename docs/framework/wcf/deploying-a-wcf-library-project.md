---
title: "WCF ライブラリ プロジェクトの配置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF ライブラリ プロジェクトの配置
ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス ライブラリ プロジェクトの配置方法について説明します。  
  
## WCF サービス ライブラリの配置  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、ダイナミックリンク ライブラリ \(DLL\) です。それ自体を単独で実行することはできません。ホスティング環境に配置する必要があります。このプロセスの詳細については、「[WCF サービスのホスティングと利用](http://go.microsoft.com/fwlink/?LinkId=99932)」を参照してください。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、他の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスと同様に配置できます。ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、DLL に対する構成はサポートされていません<xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトにより、配置中、ライブラリに App.config ファイルが提供され、この制限が緩和されます。ただし、配置後、この App.config ファイルは認識されません。  
  
 構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。