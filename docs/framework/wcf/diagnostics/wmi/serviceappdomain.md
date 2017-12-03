---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 325497435e24843cc74e804ef38e562617f27167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="serviceappdomain"></a>ServiceAppDomain
アプリケーション ドメインにサービスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceAppDomain クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceAppDomain クラスには、次のプロパティがあります。  
  
### <a name="ref"></a>ref  
 データ型 : Service  
修飾子: キー  
  
 アクセスの種類 : 読み取り専用  
  
 このアプリケーション ドメインのサービスです。  
  
### <a name="ref"></a>ref  
 データ型: AppDomainInfo  
修飾子: キー  
  
 アクセスの種類 : 読み取り専用  
  
 アプリケーション ドメインのプロパティが格納されています。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
