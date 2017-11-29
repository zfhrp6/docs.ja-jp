---
title: "暗号化クラスへのアルゴリズム名の割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e59b2551545b8b70bcb54a5d43d041c44579b786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>暗号化クラスへのアルゴリズム名の割り当て
次の 4 つの方法を開発者が、暗号化を使用してオブジェクトを作成することができますが、 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   使用してオブジェクトを作成、**新しい**演算子。  
  
-   呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成、**作成**該当するアルゴリズムの抽象クラスのメソッドです。  
  
-   呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドです。  
  
-   呼び出して、暗号アルゴリズム (対称ブロック暗号) などのクラスを実装するオブジェクトを作成、**作成**アルゴリズムの種類の抽象クラスのメソッド (など<xref:System.Security.Cryptography.SymmetricAlgorithm>)。  
  
 たとえば、開発者が、一連のバイトの SHA1 ハッシュを計算します。 <xref:System.Security.Cryptography>名前空間には、SHA1 アルゴリズム、1 つの純粋なマネージ実装および CryptoAPI をラップする 1 つの 2 つの実装が含まれています。 開発者は、特定の SHA1 実装のインスタンスを作成するを選択できます (など、 <xref:System.Security.Cryptography.SHA1Managed>) を呼び出して、**新しい**演算子。 ただし場合は、共通言語ランタイム クラスには SHA1 ハッシュ アルゴリズムを実装している限りをロードするクラスもかまいませんが、開発者は、オブジェクトを作成できますを呼び出して、<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>メソッドです。 このメソッドを呼び出す**System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**、SHA1 ハッシュ アルゴリズムの実装を返す必要があります。  
  
 開発者が呼び出すことができますも**System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")**のため、既定では、暗号化の構成には、.NET Framework に付属しているアルゴリズムの短い名前が含まれます。  
  
 ハッシュ アルゴリズムを使用する必要はない場合、開発者が呼び出すことができます、<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>ハッシュの変換を実装するオブジェクトを返すメソッド。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>構成ファイル内のアルゴリズム名の割り当てください。  
 既定では、ランタイムが返されます、 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 4 つのシナリオのオブジェクト。 ただし、コンピューターの管理者は、最後の 2 つのシナリオで、メソッドが返すオブジェクトの種類を変更できます。 これを行うには、マシン構成ファイル (Machine.config) で使用するクラスにアルゴリズムの表示名をマップする必要があります。  
  
 次の例は、ランタイムを構成する方法を示していますように**System.Security.Cryptography.SHA1.Create**、 **System.Security.CryptoConfig.CreateFromName("SHA1")**、および**。System.Security.Cryptography.HashAlgorithm.Create**を返す、`MySHA1HashClass`オブジェクト。  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 内の属性の名前を指定することができます、 [< cryptoClass\>要素](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)(前の例で、属性は名前`MySHA1Hash`)。 内の属性の値、  **\<cryptoClass >**要素は、共通言語ランタイムを使用して、クラスを検索する文字列。 指定された要件を満たす任意の文字列を使用する[完全修飾型名の指定](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。  
  
 複数のアルゴリズム名は、同じクラスにマップできます。 [ \<NameEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)クラスを 1 つのアルゴリズムの表示名にマップします。 **名前**属性が指定できるを呼び出すときに使用される文字列、 **System.Security.Cryptography.CryptoConfig.CreateFromName**メソッド、または、で抽象暗号化クラスの名前<xref:System.Security.Cryptography>名前空間。 値、**クラス**属性は、属性の名前、  **\<cryptoClass >**要素。  
  
> [!NOTE]
>  呼び出して、SHA1 アルゴリズムを取得することができます、<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>または**Security.CryptoConfig.CreateFromName("SHA1")**メソッドです。 各メソッドは、SHA1 アルゴリズムを実装するオブジェクトが返されることにのみ保証されます。 各アルゴリズムの名前を構成ファイルで同じクラスにマップする必要はありません。  
  
 既定の名前とそれらに対応付けるクラスの一覧は、次を参照してください。<xref:System.Security.Cryptography.CryptoConfig>です。  
  
## <a name="see-also"></a>関連項目  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
