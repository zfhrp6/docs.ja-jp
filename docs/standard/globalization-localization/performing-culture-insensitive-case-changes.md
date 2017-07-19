---
title: "カルチャを認識しない大文字と小文字の変更の実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "String.ToLower メソッド"
  - "カルチャ、大文字と小文字の区別"
  - "Char.ToLower メソッド"
  - "大文字と小文字、変更 (カルチャを認識しない文字列での)"
  - "Char.ToUpper メソッド"
  - "カルチャを認識しない文字列操作、大文字と小文字の変更"
  - "String.ToUpper メソッド"
  - "culture パラメーター"
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# カルチャを認識しない大文字と小文字の変更の実行
<xref:System.String.ToUpper%2A?displayProperty=fullName>、<xref:System.String.ToLower%2A?displayProperty=fullName>、<xref:System.Char.ToUpper%2A?displayProperty=fullName>、<xref:System.Char.ToLower%2A?displayProperty=fullName> の各メソッドには、パラメーターを受け取らないオーバーロードが用意されています。  既定では、パラメーターを使用しないこれらのオーバーロードは、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> の値に基づいて大文字と小文字の変更を実行します。  このため、大文字と小文字を区別する結果がカルチャによって異なる場合があります。  大文字と小文字の変更がカルチャに依存するかどうかを明確にするには、`culture` パラメーターを明示的に指定する必要があるこれらのメソッドのオーバーロードを使用する必要があります。  大文字と小文字の変更がカルチャに依存する場合は、`culture` パラメーターとして `CultureInfo.CurrentCulture` を指定します。  大文字と小文字の変更がカルチャに依存しない場合は、`culture` パラメーターとして `CultureInfo.InvariantCulture` を指定します。  
  
 後で検索しやすいように文字列の大文字と小文字を変換する場合があります。  文字列をこのように使用する場合は、`culture` パラメーターとして `CultureInfo.InvariantCulture` を指定する必要があります。<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> の値が、大文字と小文字を変更してから検索が実行されるまでの間に変更される可能性があるからです。  
  
 セキュリティに関する決定が文字列の大文字と小文字の変更操作に基づいて行われる場合は、この操作がカルチャに依存しないようにして、操作の結果が `CultureInfo.CurrentCulture` の値により影響されないようにする必要があります。  カルチャに依存した文字列操作によって矛盾した結果がどのように生成されるかを示す例については、[文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md) の記事の「現在のカルチャを使用する文字列比較」の記事を参照してください。  
  
## String.ToUpper メソッドと String.ToLower メソッドの使用  
 コードをわかりやすくするために、`culture` パラメーターを明示的に指定できる `String.ToUpper` メソッドと `String.ToLower` メソッドのオーバーロードを常に使用することをお勧めします。  識別子の検索を実行するコード例を次に示します。  `key.ToLower` 操作は既定ではカルチャを認識しますが、この動作はコードを見ても明確ではありません。  
  
### 例  
  
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
  
## Char.ToUpper メソッドと Char.ToLower メソッドの使用  
 `Char.ToUpper` メソッドおよび `Char.ToLower` メソッドはそれぞれ `String.ToUpper` メソッドおよび `String.ToLower` メソッドと同じ特性を持っていますが、影響を受けるカルチャはトルコ語 \(トルコ\) およびアゼルバイジャン語 \(ラテン、アゼルバイジャン\) だけです。  単一の文字の大文字と小文字の区別が異なるのは、この 2 つのカルチャだけです。  この固有の大文字と小文字の対応の詳細については、<xref:System.String> クラスに関するトピックの「Casing \(大文字と小文字の指定\)」を参照してください。  コードをわかりやすくし、結果の一貫性を確保するために、`culture` パラメーターを明示的に指定できるこれらのメソッドのオーバーロードを常に使用することをお勧めします。  
  
## 参照  
 <xref:System.String.ToUpper%2A?displayProperty=fullName>   
 <xref:System.String.ToLower%2A?displayProperty=fullName>   
 <xref:System.Char.ToUpper%2A?displayProperty=fullName>   
 <xref:System.Char.ToLower%2A?displayProperty=fullName>   
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)