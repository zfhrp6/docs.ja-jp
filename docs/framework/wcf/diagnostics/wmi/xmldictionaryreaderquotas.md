---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>構文  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>メソッド  
 XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 許される最大配列長。  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 1 回の読み取りで返すことができる最大バイト数。  
  
### <a name="maxdepth"></a>MaxDepth  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 1 回の読み取りでの最大ネスト ノード深度。  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 テーブル名の最大文字数。  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 XML 要素のコンテンツで許可される最大文字数。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
