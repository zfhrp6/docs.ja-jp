---
title: CustomBindingElement
ms.date: 03/30/2017
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
ms.openlocfilehash: 2261af592120eac65923108ed5a20265fccb6b4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485506"
---
# <a name="custombindingelement"></a>CustomBindingElement
CustomBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## <a name="methods"></a>メソッド  
 CustomBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 CustomBindingElement クラスには、次のプロパティがあります。  
  
### <a name="name"></a>名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの構成名を格納する文字列です。 この値は、カスタム バインディングの識別文字列として機能するユーザー定義文字列です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.CustomBinding>
