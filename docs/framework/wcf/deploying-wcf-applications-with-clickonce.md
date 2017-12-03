---
title: "ClickOnce を使用して WCF アプリケーションを展開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 714e8341c58e5337d8e45bf61b48137d33fa51b9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-wcf-applications-with-clickonce"></a>ClickOnce を使用して WCF アプリケーションを展開する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] を使用しているクライアント アプリケーションは、ClickOnce テクノロジを使用して展開できます。 このテクノロジを使用すると、クライアント アプリケーションが、信頼できる証明書でデジタル署名されている場合、コード アクセス セキュリティによって提供されるランタイム セキュリティ保護を受けられます。 ClickOnce アプリケーションの署名に使用される証明書は、信頼された発行者のストアに存在する必要があり、またそのクライアント コンピューターのローカル セキュリティ ポリシーでは、発行者の証明書で署名されたアプリケーションに対して、完全信頼のアクセス許可が構成される必要があります。  
  
 ClickOnce アプリケーションおよび信頼できる発行元の構成方法の詳細については、次を参照してください。 [ClickOnce 信頼された発行元の構成](http://go.microsoft.com/fwlink/?LinkId=94774)です。  
  
## <a name="see-also"></a>関連項目  
 [信頼されたアプリケーションの配置の概要](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [ClickOnce 配置の Windows フォーム アプリケーション](http://go.microsoft.com/fwlink/?LinkId=94776)
