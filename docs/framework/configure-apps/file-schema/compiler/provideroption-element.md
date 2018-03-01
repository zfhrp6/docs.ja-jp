---
title: "&lt;providerOption&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f28b7b43f2f782744a0dbc81bd0b91bbbcd8abba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt;要素
言語プロバイダーのコンパイラ バージョン属性を指定します。  
  
 \<構成要素 >  
\<system.codedom Element>  
\<コンパイラ要素 >  
\<コンパイラ > 要素  
\<providerOption > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> オプションの名前を指定しますたとえば、"CompilerVersion"です。|  
|`value`|必須の属性です。<br /><br /> オプションの値を指定しますたとえば、"v3.5"とします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
|[\<コンパイラ > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。|  
|[\<compiler> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|言語プロバイダーのコンパイラ構成属性を指定します。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework version 3.5 では、Code Document Object Model (CodeDOM) のコード プロバイダーをサポートしますプロバイダー固有のオプションを使用して、`<providerOption>`要素。  
  
 .NET Framework 3.5 では、更新された .NET Framework 2.0 アセンブリに含まれてし、新しい型を含む新しいバージョン 3.5 のアセンブリを提供します。 Microsoft c# および Visual Basic コード プロバイダーは、.NET Framework 2.0 アセンブリに含まれるが、version 3.5 のコンパイラをサポートするために更新されました。 既定では、更新されたコード プロバイダーは、バージョン 2.0 コンパイラ用のコードを生成します。 使用することができます、 `<providerOption>` 3.5 をターゲット コンパイラのバージョンを変更する要素。 これを行うには、"CompilerVersion"を指定、`name`属性との"v3.5"、`value`属性。 小文字の"v"のバージョン番号の前にする必要があります。  
  
 ことができます、バージョン指定グローバル追加することによって、`<providerOption>`を .NET Framework 2.0 Machine.config またはルートの Web.config ファイルの要素。 場合は、Machine.config ファイルに 3.5 に既定のコンパイラのバージョンを更新することができますに変更する戻る、アプリケーションごとに 2.0 を使用して、`<providerOption>`アプリケーション構成ファイル内の要素。  
  
 CodeDOM コード プロバイダーの実装側を受け取るコンス トラクターを提供することによってカスタム オプションを処理できる、`providerOptions`型のパラメーター<xref:System.Collections.Generic.IDictionary%602>です。  
  
## <a name="example"></a>例  
 次の例では、そのバージョン 3.5 の c# コード プロバイダーを使用する必要がありますを指定する方法を示します。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<コンパイラ > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [コンパイル (ASP.NET 設定スキーマ) のコンパイラのコンパイラ要素](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
