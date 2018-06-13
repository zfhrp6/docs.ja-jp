---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484330"
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
