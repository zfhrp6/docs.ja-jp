---
title: "ClickOnce を使用して WCF アプリケーションを展開する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ClickOnce を使用して WCF アプリケーションを展開する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] を使用しているクライアント アプリケーションは、ClickOnce テクノロジを使用して展開できます。このテクノロジを使用すると、クライアント アプリケーションが、信頼できる証明書でデジタル署名されている場合、コード アクセス セキュリティによって提供されるランタイム セキュリティ保護を受けられます。ClickOnce アプリケーションの署名に使用される証明書は、信頼された発行者のストアに存在する必要があり、またそのクライアント コンピューターのローカル セキュリティ ポリシーでは、発行者の証明書で署名されたアプリケーションに対して、完全信頼のアクセス許可が構成される必要があります。  
  
 ClickOnce アプリケーションの構成と信頼された発行者の詳細については、「[Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774)」を参照してください。  
  
## 参照  
 [信頼されたアプリケーションの配置の概要](http://go.microsoft.com/fwlink/?LinkId=94775)   
 [Windows フォーム アプリケーションの ClickOnce 配置](http://go.microsoft.com/fwlink/?LinkId=94776)