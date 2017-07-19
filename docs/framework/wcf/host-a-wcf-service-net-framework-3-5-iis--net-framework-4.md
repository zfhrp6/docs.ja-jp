---
title: ".NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# .NET Framework 4 で実行されている IIS 内の .NET Framework 3.5 で作成された WCF サービスをホストする方法
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] を実行するコンピューターで [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] を使用して作成された [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスをホストすると、次のテキストで <xref:System.ServiceModel.ProtocolException> が返される場合があります。  
  
```Output  
ハンドルされていない例外: System.ServiceModel.ProtocolException: 応答メッセージのコンテンツの種類 text/html; charset=utf-8 が、バインド (application/soap+xml; charset=utf-8) のコンテンツの種類と一致しません。カスタム エンコーダーを使用している場合は、IsContentTypeSupported メソッドが正しく実装されていることを確認してください。応答の先頭の 1024 バイトは '<html>    <head>        <title>' でした。アプリケーション ドメインまたはアプリケーション プールは、現在、バージョン 4 以降の .NET Framework を実行しています。この Web アプリケーションの IIS 設定が 4.0 以降に設定されている場合、または ASP.NET Web 開発サーバーのバージョン 4.0 以降を使用している場合に、この状況が発生することがあります。この Web アプリケーションの Web.config ファイル内の <compilation> 要素に、このバージョンの .NET Framework に必要な targetFrameworkMoniker 属性が含まれていません (<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"&gt, など)。この属性を使用して Web.config ファイルを更新するか、別のバージョンの .NET Framework を使用するように Web アプリケーションを構成します。</title>...  
```  
  
 または、サービスの .svc ファイルを参照する際に、次のテキストのエラー ページが表示される場合があります。  
  
```Output  
アプリケーション ドメインまたはアプリケーション プールは、現在、.NET Framework のバージョン 4.0 以降を実行しています。この Web アプリケーションの IIS 設定が 4.0 以降に設定されている場合、または ASP.NET Web 開発サーバーのバージョン 4.0 以降を使用している場合に、この状況が発生することがあります。この Web アプリケーションの Web.config ファイル内の <compilation> 要素に、このバージョンの .NET Framework に必要な targetFrameworkMoniker 属性が含まれていません ('<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">' など)。この属性を使用して Web.config ファイルを更新するか、別のバージョンの .NET Framework を使用するように Web アプリケーションを構成します。  
```  
  
 これらのエラーは、IIS が実行されているアプリケーション ドメインが [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] を実行していて、WCF サービスが [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] で実行されるように構成されている場合に発生します。このトピックでは、このサービスを実行するために必要な変更について説明します。  
  
 次に、\<`compilers`\> 要素を検索し、CompilerVersion プロバイダー オプションの値を 4.0 に変更します。既定では、2 つの \<`compiler`\> 要素が \<`compilers`\> 要素にあります。次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。  
  
```  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### 必要な targetFramework 属性の追加  
  
1.  サービスの Web.config ファイルを開き、\<`compilation`\> 要素を探します。  
  
2.  次の例に示すように、`targetFramework` 属性を \<`compilation`\> 要素に追加します。  
  
    ```  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  \<`compilers`\> 要素を検索し、CompilerVersion プロバイダー オプションの値を 4.0 に変更します。既定では、2 つの \<`compiler`\> 要素が \<`compilers`\> 要素にあります。次の例に示すように、両方の CompilerVersion プロバイダー オプションを更新する必要があります。  
  
    ```  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```