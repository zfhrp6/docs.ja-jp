---
title: '方法: 自動バインディング リダイレクトを有効/無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d71da1b48938f9f98221d86f0f9badee3a17919
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a>方法: 自動バインディング リダイレクトを有効/無効にする
[!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]以降では、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]を対象とするアプリをコンパイルするときに、アセンブリの統一をオーバーライドするために、アプリ構成ファイルにバインド リダイレクトが自動的に追加される場合があります。 アプリの構成ファイルで手動でバインド リダイレクトを指定している場合でも、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、バインド リダイレクトが追加されます。 自動バインド リダイレクト機能は、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象とする従来のデスクトップ アプリと Web アプリに影響します。ただし、Web アプリに対する動作は若干異なります。 以前のバージョンの .NET Framework を対象とする既存のアプリがある場合は、自動バインド リダイレクトを有効にできます。また、手動で作成したバインド リダイレクトを保持する場合は、この機能を無効にできます。  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a>デスクトップ アプリでの自動バインド リダイレクトの無効化  
 自動バインド リダイレクトは、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 以上のバージョンを対象とする従来のデスクトップ アプリで、既定で有効になっています。 バインド リダイレクトは、アプリケーションがコンパイルされ、発生する可能性のあるアセンブリの統一をオーバーライドするときに、出力構成ファイル (app.config) に追加されます。 ソース app.config ファイルは変更されません。 アプリのプロジェクト ファイルを変更して、この機能を無効にできます。  
  
#### <a name="to-disable-automatic-binding-redirects"></a>自動バインド リダイレクトを無効にするには  
  
1.  Visual studio でプロジェクトを選択**ソリューション エクスプ ローラー**を選択し**ファイル エクスプ ローラーでフォルダーを開く**ショートカット メニューからです。  
  
2.  エクスプローラーで、プロジェクト ファイル (.csproj または .vbproj) を検索し、メモ帳で開きます。  
  
3.  プロジェクト ファイルで、次のプロパティ エントリを検索します。  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  `true` を `false` に変更します。  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a>自動バインド リダイレクトの手動での有効化  
 自動バインド リダイレクトは、.NET Framework の旧バージョンを対象とする既存のアプリで有効にするか、またはリダイレクトの追加を確認するメッセージが自動的に表示されない場合に有効にできます。 新しいバージョンのフレームワークを対象としているが、リダイレクトの追加を確認するメッセージが自動的に表示されない場合は、ビルド出力でアセンブリを再マップすることが推奨されることがあります。  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a>自動バインド リダイレクトのプロパティを手動で追加するには  
  
1.  Visual studio でプロジェクトを選択**ソリューション エクスプ ローラー**を選択し**ファイル エクスプ ローラーでフォルダーを開く**ショートカット メニューからです。  
  
2.  エクスプローラーで、プロジェクト ファイル (.csproj または .vbproj) を検索し、メモ帳で開きます。  
  
3.  次の要素を最初の構成プロパティ グループに追加 (下にある、 \<PropertyGroup > タグ)。  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     要素が挿入されたプロジェクト ファイルの例を次に示します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProjectGuid>{123334}</ProjectGuid>  
        ...  
        <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>  
      </PropertyGroup>  
    ...  
    </Project>  
    ```  
  
4.  アプリをコンパイルします。  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a>Web アプリでの自動バインド リダイレクトの有効化  
 自動バインド リダイレクトは、Web アプリでは異なる方法で実装されます。 ソースの構成 (web.config) ファイルを Web アプリ用に変更する必要があるため、バインド リダイレクトは構成ファイルに自動的に追加されません。 ただし、Visual Studio によってバインドの競合が通知されるため、バインド リダイレクトを追加して競合を解決できます。 バインド リダイレクトを追加するかどうかの確認メッセージは常に表示されるため、明示的に Web アプリのこの機能を無効にする必要はありません。  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a>web.config ファイルにバインド リダイレクトを追加するには  
  
1.  Visual Studio で、アプリをコンパイルし、ビルドの警告を確認します。  
  
     ![ビルドのアセンブリ参照の競合を警告](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")  
  
2.  アセンブリ バインドの競合がある場合、警告が表示されます。 警告をダブルクリックします  (キーボード: 警告とキーを押して選択**Enter**)。  
  
     自動的にソース web.config ファイルに必要なバインド リダイレクトを追加できるダイアログ ボックスが表示されます。  
  
     ![バインディング リダイレクトのアクセス許可ダイアログ](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")  
  
## <a name="see-also"></a>関連項目  
 [\<bindingRedirect > 要素](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
