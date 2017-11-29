---
title: "&lt;コンパイラ&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8d2562bb37413cd07b4548bbf2bad0b6a9aedbc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilergt-element"></a>&lt;コンパイラ&gt;要素
言語プロバイダーのコンパイラ構成属性を指定します。  
  
 \<構成要素 >  
\<system.codedom 要素 >  
\<コンパイラ要素 >  
\<コンパイラ > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`compilerOptions`|省略可能な属性です。<br /><br /> コンパイルのコンパイラ固有の追加の引数を指定します。 値、`compilerOptions`属性は通常はコンパイラのコンパイラ オプションのトピックに表示します。 Visual Studio 2005 ドキュメントでの「コンパイラ オプション」というキーワードを検索してコンパイラのオプションを検索できます。|  
|`extension`|必須の属性です。<br /><br /> 言語プロバイダーのソース ファイルによって使用されるファイル名拡張子のセミコロンで区切った一覧を示します。 たとえば、".cs"と指定します。|  
|`language`|必須の属性です。<br /><br /> 言語プロバイダーによってサポートされる言語名のセミコロン区切りの一覧を提供します。 たとえば、「c# 以外の場合は cs; csharp」です。|  
|`type`|必須の属性です。<br /><br /> プロバイダーの実装を含むアセンブリの名前を含め、言語プロバイダーの型名を指定します。 型名で定義されている要件を満たす必要がある[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)です。|  
|`warningLevel`|省略可能な属性です。<br /><br /> 既定のコンパイラ警告レベルを指定しますある言語プロバイダーは、コンパイルの警告をエラーとして扱いますレベルが決まります。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<providerOption > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|言語プロバイダーのコンパイラ バージョン属性を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|使用可能な言語プロバイダーのコンパイラ構成設定を指定します。|  
|[\<コンパイラ > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラ構成要素のコンテナー0 個以上含む`<compiler>`要素。|  
  
## <a name="remarks"></a>コメント  
 各`<compiler>`要素は、特定の言語プロバイダーのコンパイラ構成属性を指定します。 プロバイダーでは、 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 、特定の言語のクラス、`<compiler>`要素は、コンパイラおよび言語プロバイダーのコード ジェネレーターの設定を定義します。  
  
 .NET Framework は、マシン構成ファイル (Machine.config) 内でコンパイラの初期設定を定義します。 開発者やコンパイラ ベンダーは、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> の実装のために構成設定を追加することができます。 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってコンピューターの言語プロバイダーとコンパイラ構成の設定を列挙します。  
  
 アプリケーションまたは Web 構成ファイル内のコンパイラ要素では、補完したり、コンピューターの構成ファイル設定を上書きすることができます。 1 つ以上のプロバイダー実装が同じ言語の名前または同じのファイル拡張子に対して構成されている場合、最後の一致する構成は、その言語名またはファイル拡張子の前の構成済みのプロバイダーをオーバーライドします。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、一般的なコンパイラ構成要素を示しています。  
  
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
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<コンパイラ > 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [コンパイル (ASP.NET 設定スキーマ) のコンパイラのコンパイラ要素](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
