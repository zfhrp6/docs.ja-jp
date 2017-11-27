---
title: "&lt;system.codedom&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8b223ab6ab742c5b7d3b3d2f5640e99835afe268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemcodedomgt-element"></a>&lt;system.codedom&gt;要素
使用可能な言語プロバイダーのコンパイラ構成設定を指定します。  
  
 \<configuration > 要素  
\<system.codedom > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|0 個以上の [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 要素を含むコンパイラ構成要素のコンテナー。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="net-framework-version-20"></a>.NET framework Version 2.0  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素にはなど、.NET Framework と共にインストールされる既定のプロバイダーだけでなく、コンピューターにインストールされている言語プロバイダーのコンパイラ構成設定が含まれています、<xref:Microsoft.CSharp.CSharpCodeProvider>と<xref:Microsoft.VisualBasic.VBCodeProvider>です。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。 各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
 開発者やコンパイラ ベンダーできます構成設定を追加、マシン構成ファイル (Machine.config) に、新しい<xref:System.CodeDom.Compiler.CodeDomProvider>実装します。 使用して、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType>プログラムで、既定の言語プロバイダーと、コンピューターのコンパイラ構成設定によって識別される言語プロバイダーを列挙するメソッド。  
  
> [!NOTE]
>  .NET Framework version 1.0 および 1.1 では、既定の言語で、.NET Framework で提供されるプロバイダーを識別、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素。 .NET framework version 2.0 では、既定の言語プロバイダーとして指定されていないで、 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素を使用して列挙できますが、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>メソッドです。  
  
## <a name="net-framework-versions-10-and-11"></a>.NET framework のバージョン 1.0 および 1.1  
 [ \<System.codedom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)要素には、コンピューター上の言語プロバイダーの構成設定コンパイラにはが含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)要素は、0 個以上含まれています。 [\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素。 各[\<コンパイラ >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。  
  
 .NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、一般的なコンパイラ構成を示しています。  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [コンパイラおよび言語プロバイダー設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<compiler> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
