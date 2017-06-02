---
title: "暗号化クラスへのアルゴリズム名の割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "暗号アルゴリズム"
  - "暗号化, 割り当て (アルゴリズム名の)"
  - "割り当て (アルゴリズム名の)"
  - "名前 [.NET Framework], アルゴリズムの割り当て"
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 暗号化クラスへのアルゴリズム名の割り当て
開発者は、[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] を使用して、次の 4 とおりの方法で暗号オブジェクトを作成できます。  
  
-   **new** 演算子を使用してオブジェクトを作成する。  
  
-   アルゴリズムの抽象クラスの **Create** メソッドを呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成する。  
  
-   [System.Security.Cryptography.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic) メソッドを呼び出して、特定の暗号化アルゴリズムを実装するオブジェクトを作成する。  
  
-   暗号化アルゴリズムの抽象クラス \(<xref:System.Security.Cryptography.SymmetricAlgorithm> など\) の **Create** メソッドを呼び出して、その種類の暗号化アルゴリズム \(対称ブロック暗号法など\) のクラスを実装するオブジェクトを作成する。  
  
 たとえば、開発者が、バイト セットの SHA1 ハッシュを計算すると仮定します。  <xref:System.Security.Cryptography> 名前空間には、SHA1 アルゴリズムの 2 つの実装が含まれています。1 つは純粋なマネージ実装であり、もう 1 つは CryptoAPI をラップする実装です。  開発者は、**new** 演算子を呼び出すことにより、特定の SHA1 実装 \([SHA1Managed クラス](frlrfSystemSecurityCryptographySHA1ManagedClassTopic)など\) をインスタンス化できます。  しかし、そのクラスが SHA1 ハッシュ アルゴリズムを実装していれば共通言語ランタイムがどのクラスを読み込むかは問題でない場合、開発者は [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic) メソッドを呼び出してオブジェクトを作成できます。  このメソッドは、SHA1 ハッシュ アルゴリズムの実装を返す **System.Security.Cryptography.CryptoConfig.CreateFromName\("System.Security.Cryptography.SHA1"\)** を呼び出します。  
  
 暗号構成には、既定として、.NET Framework に付属しているアルゴリズムのための短い名前が含まれているため、開発者は **System.Security.Cryptography.CryptoConfig.CreateFromName\("SHA1"\)** を呼び出すこともできます。  
  
 どのハッシュ アルゴリズムを使用するかは問題でない場合、開発者はハッシュ変換を実装するオブジェクトを返す [System.Security.Cryptography.HashAlgorithm.Create](frlrfSystemSecurityCryptographyHashAlgorithmClassCreateTopic) メソッドを呼び出すことができます。  
  
## 構成ファイル内でのアルゴリズム名の割り当て  
 既定では、ランタイムは 4 つのシナリオのいずれの場合にも、[System.Security.Cryptography.SHA1CryptoServiceProvider クラス](frlrfSystemSecurityCryptographySHA1CryptoServiceProviderClassTopic) オブジェクトを返します。  コンピューター管理者は、後の 2 つのシナリオのメソッドが返すオブジェクトの型を変更できます。  オブジェクトの型を変換するには、マシン構成ファイル \(Machine.config\) 内で、使用するクラスにアルゴリズムの表示名を割り当てる必要があります。  
  
 **System.Security.Cryptography.SHA1.Create**、**System.Security.CryptoConfig.CreateFromName\("SHA1"\)**、および **System.Security.Cryptography.HashAlgorithm.Create** が `MySHA1HashClass` オブジェクトを返すようにランタイムを設定する方法の例を次に示します。  
  
```  
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
  
 [\<cryptoClass\> 要素](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) に属性名を指定できます。上の例では、属性 `MySHA1Hash`を指定します\)。  **\<cryptoClass\>** 要素の属性の値は、共通言語ランタイム クラスを検索するために使用する文字列です。  「[完全限定型名の指定](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」に指定されている要件を満たす任意の文字列を使用できます。  
  
 同一のクラスに複数のアルゴリズム名を割り当てることができます。  [\<nameEntry\> 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) は 1 個のわかりやすいアルゴリズムにクラス名を割り当てます。  **name** 属性は、**System.Security.Cryptography.CryptoConfig.CreateFromName** メソッドを呼び出すときに使用する文字列または <xref:System.Security.Cryptography> 名前空間の抽象暗号化クラスです。  **class** 属性の値は **\<cryptoClass\>** 要素内の属性の名前です。  
  
> [!NOTE]
>  [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic) メソッドまたは **Security.CryptoConfig.CreateFromName\("SHA1"\)** メソッドを呼び出すことにより SHA1 アルゴリズムを取得できます。  それぞれのメソッドで保証されるのは、SHA1 アルゴリズムを実装するオブジェクトを返すことだけです。  構成ファイル内の同じクラスに、アルゴリズムのそれぞれの表示名を割り当てる必要はありません。  
  
 既定の名前の一覧およびそれらの名前を割り当てるクラスについては、「[CryptoConfig クラス](frlrfSystemSecurityCryptographyCryptoConfigClassTopic)」を参照してください。  
  
## 参照  
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)   
 [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)