---
title: "暗号署名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "暗号化 [.NET Framework], シグネチャ"
  - "デジタル署名"
  - "デジタル署名, 概要"
  - "デジタル署名, 生成"
  - "デジタル署名, 検査"
  - "デジタル署名, XML 署名"
  - "暗号化 [.NET Framework], シグネチャ"
  - "生成 (署名を)"
  - "セキュリティ [.NET Framework], シグネチャ"
  - "シグネチャ, 暗号化"
  - "署名 (XML に)"
  - "検査 (署名を)"
  - "XML 署名"
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 暗号署名
<a name="top"></a> 暗号デジタル署名は、公開キー アルゴリズムを使用してデータの整合性を提供します。 デジタル署名を使用してデータに署名すると、第三者が署名を検証し、データが署名者から発信され、署名後に変更されていないことを証明できます。 デジタル署名の詳細については、「[暗号サービス](../../../docs/standard/security/cryptographic-services.md)」を参照してください。  
  
 ここでは、<xref:System.Security.Cryptography?displayProperty=fullName> 名前空間のクラスを使用してデジタル署名を生成して検証する方法について説明します。  
  
-   [署名の生成](#generate)  
  
-   [署名の検証](#verify)  
  
<a name="generate"></a>   
## 署名の生成  
 デジタル署名は、通常、大きなデータを表現するハッシュ値に適用されます。 ハッシュ値にデジタル署名を適用する例を次に示します。 まず、<xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスの新しいインスタンスを作成して、公開キー\/秘密キーのペアを生成します。 次に、<xref:System.Security.Cryptography.RSACryptoServiceProvider> を <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスの新しいインスタンスに渡します。 これにより、デジタル署名を実際に実行する <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> に秘密キーが渡されます。 ハッシュ コードに署名するためには、使用するハッシュ アルゴリズムを指定する必要があります。 この例では、SHA1 アルゴリズムを使用します。 最後に、<xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> メソッドを呼び出して署名を実行します。  
  
```vb  
Imports System Imports System.Security.Cryptography Module Module1 Sub Main() 'The hash value to sign. Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135} 'The value to hold the signed value. Dim SignedHashValue() As Byte 'Generate a public/private key pair. Dim RSA As New RSACryptoServiceProvider() 'Create an RSAPKCS1SignatureFormatter object and pass it 'the RSACryptoServiceProvider to transfer the private key. Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA) 'Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1") 'Create a signature for HashValue and assign it to 'SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue) End Sub End Module using System; using System.Security.Cryptography;  
  
```  
  
```csharp  
class Class1 { static void Main() { //The hash value to sign. byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135}; //The value to hold the signed value. byte[] SignedHashValue; //Generate a public/private key pair. RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); //Create an RSAPKCS1SignatureFormatter object and pass it the //RSACryptoServiceProvider to transfer the private key. RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA); //Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1"); //Create a signature for HashValue and assign it to //SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue); } }  
```  
  
### XML ファイルへの署名  
 .NET Framework に用意されている <xref:System.Security.Cryptography.Xml> 名前空間を使用すると、XML に署名できます。 XML が特定のソースから送信されたことを検証する場合は、XML への署名が重要です。 たとえば、XML を使用する株価情報サービスを使用している場合であれば、署名されているかどうかによって XML のソースを検証できます。  
  
 この名前空間のクラスは、World Wide Web コンソーシアムの「[XML 署名の構文と処理に関する勧告](http://go.microsoft.com/fwlink/?LinkId=136777)」に従っています。  
  
 [ページのトップへ](#top)  
  
<a name="verify"></a>   
## 署名の検証  
 データが特定の関係者によって署名されたことを検証するには、次の情報が必要です。  
  
-   データに署名した関係者の公開キー。  
  
-   デジタル署名。  
  
-   署名されたデータ。  
  
-   署名者が使用したハッシュ アルゴリズム。  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> クラスによって署名された署名を検証するには、<xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスを使用します。<xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> クラスに対しては、署名者の公開キーを提供する必要があります。 公開キーを指定するには、剰余値と指数部の値が必要になります  \(これらの値は、公開キーと秘密キーのペアの作成者が提供する必要があります\)。 まず、署名を検証する公開キーを保持するための <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを作成します。次に、<xref:System.Security.Cryptography.RSAParameters> 構造体を、公開キーを指定する剰余値と指数部の値で初期化します。  
  
 次のコードは、<xref:System.Security.Cryptography.RSAParameters> 構造体の作成を示しています。`Modulus` プロパティは `ModulusData` というバイト配列の値に設定し、`Exponent` プロパティは `ExponentData` というバイト配列の値に設定します。  
  
```vb  
Dim RSAKeyInfo As RSAParameters RSAKeyInfo.Modulus = ModulusData RSAKeyInfo.Exponent = ExponentData  
  
```  
  
```csharp  
RSAParameters RSAKeyInfo; RSAKeyInfo.Modulus = ModulusData; RSAKeyInfo.Exponent = ExponentData;  
```  
  
 <xref:System.Security.Cryptography.RSAParameters> オブジェクトを作成した後、<xref:System.Security.Cryptography.RSACryptoServiceProvider> クラスの新しいインスタンスを <xref:System.Security.Cryptography.RSAParameters> で指定した値に初期設定できます。 次に、<xref:System.Security.Cryptography.RSACryptoServiceProvider> を <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> のコンストラクターに渡してキーを転送します。  
  
 このプロセスを説明する例を次に示します。 この例で、`HashValue` と `SignedHashValue` は、リモートにいる関係者から提供されるバイト配列です。 リモートにいる関係者は、SHA1 アルゴリズムを使用して `HashValue` に署名し、デジタル署名 `SignedHashValue` を生成します。 、  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=fullName> メソッドは、デジタル署名が有効であることと、そのデジタル署名を使用して `HashValue` が署名されたことを検証します。  
  
```vb  
Dim RSA As New RSACryptoServiceProvider() RSA.ImportParameters(RSAKeyInfo) Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA) RSADeformatter.SetHashAlgorithm("SHA1") If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then Console.WriteLine("The signature is valid.") Else Console.WriteLine("The signture is not valid.") End If  
  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); RSA.ImportParameters(RSAKeyInfo); RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA); RSADeformatter.SetHashAlgorithm("SHA1"); if(RSADeformatter.VerifySignature(HashValue, SignedHashValue)) { Console.WriteLine("The signature is valid."); } else { Console.WriteLine("The signature is not valid."); }  
```  
  
 上記のコードでは、署名が有効であれば "`The signature is valid`" を表示し、署名が無効であれば "`The signature is not valid`" を表示します。  
  
## 参照  
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)