---
title: AspNetCompatibilityRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00908a39-a21b-4029-bbb9-33e5a6ed25a7
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29ab9cf69ca7ccef82ed21f505d309d6a641ce8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="aspnetcompatibilityrequirementsattribute"></a>AspNetCompatibilityRequirementsAttribute
AspNetCompatibilityRequirementsAttribute  
  
## <a name="syntax"></a>構文  
  
```  
class AspNetCompatibilityRequirementsAttribute : Behavior  
{  
  string RequirementsMode;  
};  
```  
  
## <a name="methods"></a>メソッド  
 AspNetCompatibilityRequirementsAttribute クラスは、メソッドをすべて定義しません。  
  
## <a name="properties"></a>プロパティ  
 AspNetCompatibilityRequirementsAttribute クラスには、次のプロパティがあります。  
  
### <a name="requirementsmode"></a>RequirementsMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 Asp.Net 互換モードがアクティブであるかどうかを示します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceHostingEnvironment.AspNetCompatibilityEnabled%2A>
