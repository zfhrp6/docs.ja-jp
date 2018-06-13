---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 78914d52a9e57fe2e48adcfc0d7b6f911a0d8b3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487829"
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
