---
title: 3501 - InferredContractDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32eac2fbfc0175010906d600b2d044868bda38be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3501---inferredcontractdescription"></a>3501 - InferredContractDescription
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|3501|  
|キーワード|WFServices|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 ContractDescription が WorkflowService から推論されたことを示します。  
  
## <a name="message"></a>メッセージ  
 Name='%1' で Namespace='%2' の ContractDescription が WorkflowService から推論されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|名前|xs:string|ContractDescription の名前。|  
|Namespace|xs:string|ContractDescription の名前空間。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
