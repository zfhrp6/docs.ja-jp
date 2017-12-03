---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f576c2f82590f683aa51d5cc70c67a4a2b15a1e0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
エンドポイントにサービスを割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceToEndpointAssociation クラスには、次のプロパティがあります。  
  
### <a name="ref"></a>ref  
 データ型 : Service  
  
 アクセスの種類 : 読み取り専用  
修飾子: キー  
  
 エンドポイントに関連付けられるサービス。  
  
### <a name="ref"></a>ref  
 データ型 : Endpoint  
  
 アクセスの種類 : 読み取り専用  
修飾子: キー  
  
 サービスに関連付けられるエンドポイント。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|
