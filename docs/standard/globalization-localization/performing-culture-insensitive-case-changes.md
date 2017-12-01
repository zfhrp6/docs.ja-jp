---
title: "カルチャを認識しない大文字と小文字の変更の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a>カルチャを認識しない大文字と小文字の変更の実行
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、<xref:System.Char.ToLower%2A?displayProperty=nameWithType> の各メソッドには、パラメーターを受け取らないオーバーロードが用意されています。 既定では、パラメーターを使用しないこれらのオーバーロードは、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> の値に基づいて大文字と小文字の変更を実行します。 このため、大文字と小文字を区別する結果がカルチャによって異なる場合があります。 大文字と小文字の変更がカルチャに依存するかどうかを明確にするには、`culture` パラメーターを明示的に指定する必要があるこれらのメソッドのオーバーロードを使用する必要があります。 大文字と小文字の変更がカルチャに依存する場合は、`CultureInfo.CurrentCulture` パラメーターとして `culture` を指定します。 大文字と小文字の変更がカルチャに依存しない場合は、`CultureInfo.InvariantCulture` パラメーターとして `culture` を指定します。  
  
 後で検索しやすいように文字列の大文字と小文字を変換する場合があります。 文字列をこのように使用する場合は、`CultureInfo.InvariantCulture` パラメーターとして `culture` を指定する必要があります。<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> の値が、大文字と小文字を変更してから検索が実行されるまでの間に変更される可能性があるからです。  
  
 セキュリティに関する決定が文字列の大文字と小文字の変更操作に基づいて行われる場合は、この操作がカルチャに依存しないようにして、操作の結果が `CultureInfo.CurrentCulture` の値により影響されないようにする必要があります。 「文字列比較を使用して、現在のカルチャ」を参照してください、[文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md)アーティクルに対してどのカルチャに依存した文字列の操作を示す例は、矛盾する結果を生成できます。  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>String.ToUpper メソッドと String.ToLower メソッドの使用  
 コードをわかりやすくするために、`String.ToUpper` パラメーターを明示的に指定できる `String.ToLower` メソッドと `culture` メソッドのオーバーロードを常に使用することをお勧めします。 識別子の検索を実行するコード例を次に示します。 `key.ToLower` 操作は既定ではカルチャを認識しますが、この動作はコードを見ても明確ではありません。  
  
### <a name="example"></a>例  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 `key.ToLower` 操作がカルチャに依存しないようにする場合は、前の例を次のように変更して、大文字と小文字を変更するときに明示的に `CultureInfo.InvariantCulture` を使用します。  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Char.ToUpper メソッドと Char.ToLower メソッドの使用  
 `Char.ToUpper`と`Char.ToLower`メソッドと同じ特性があります、`String.ToUpper`と`String.ToLower`メソッド、影響を受けるカルチャだけはトルコ語 (トルコ) およびアゼルバイジャン語 (ラテン、アゼルバイジャン)。 単一の文字の大文字と小文字の区別が異なるのは、この 2 つのカルチャだけです。 この固有の大文字と小文字の対応の詳細については、<xref:System.String> クラスに関するトピックの「Casing (大文字と小文字の指定)」を参照してください。 コードをわかりやすくし、結果の一貫性を確保するために、`culture` パラメーターを明示的に指定できるこれらのメソッドのオーバーロードを常に使用することをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
