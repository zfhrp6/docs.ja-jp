---
title: "方法 : アプリケーション ドメインを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション ドメイン, 構成"
  - "ApplicationBase プロパティ"
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : アプリケーション ドメインを構成する
<xref:System.AppDomainSetup> クラスを使用して、共通言語ランタイムに新しいアプリケーション ドメインの構成情報を提供できます。  独自のアプリケーション ドメインを作成するときに最も重要なプロパティは、<xref:System.AppDomainSetup.ApplicationBase%2A> です。  **AppDomainSetup** の他のプロパティは、主にランタイム ホストが特定のアプリケーション ドメインを構成するために使用されます。  
  
 **ApplicationBase** プロパティは、アプリケーションのルート ディレクトリを定義します。  ランタイムが型要求を満たす必要がある場合、ランタイムは **ApplicationBase** プロパティで指定したディレクトリ内でその型を含むアセンブリを調査します。  
  
> [!NOTE]
>  新しいアプリケーション ドメインは、作成元の **ApplicationBase** プロパティだけを継承します。  
  
 **AppDomainSetup** クラスのインスタンスを作成する例を次に示します。このクラスを使用してアプリケーション ドメインを新しく作成し、情報をコンソールに書き込んでから、このアプリケーション ドメインをアンロードします。  
  
## 使用例  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## 参照  
 [Hosting Overview](http://msdn.microsoft.com/ja-jp/ea527626-99e3-4995-81c4-c8f3e60eb6d5)   
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)