---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485669"
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
