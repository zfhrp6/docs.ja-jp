---
title: "方法 : WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "調整 (コンテンツの有効期限の設定を)"
  - "アプリケーション, 配置"
  - "構成 (WPF アプリケーションを配置するために Web サーバーを)"
  - "コンテンツの有効期限の設定, 調整"
  - "配置 (アプリケーションを)"
  - "ファイルの拡張子, 登録"
  - "MIME タイプ, 登録"
  - "登録 (ファイル拡張子を)"
  - "登録 (MIME タイプを)"
  - "Web サーバー, 構成 (WPF アプリケーションを配置するために)"
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する
適切な [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] タイプを使用して構成されていれば、ほとんどの Web サーバーから [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションを配置することができます。  既定では、[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] はこれらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを使用して構成されますが、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] や [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] は使用しません。  
  
 ここでは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] および [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] を構成して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを配置する方法について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
> [!NOTE]
>  レジストリ内の *UserAgent* 文字列をチェックして、システムに [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを確認します。  詳細情報と *UserAgent* 文字列を調べてシステムに [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを確認するスクリプトについては、「[.NET Framework 3.0 がインストールされているかどうかの確認](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)」を参照してください。  
  
<a name="content_expiration"></a>   
## コンテンツの有効期限の設定を調整する  
 コンテンツの有効期限の設定を 1 分に調整する必要があります。  次の手順では、[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] を使用して調整する方法について説明します。  
  
1.  \[Start\] ボタンをクリックし、\[Administrative Tools\] をポイントして、\[Internet Information Services \(IIS\) Manager\] をクリックします。  このアプリケーションは、コマンド ラインで、「%SystemRoot%\\system32\\inetsrv\\iis.msc」と入力して起動することもできます。  
  
2.  \[Default Web site\] ノードが見つかるまで [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] ツリーを展開します。  
  
3.  \[Default Web site\] を右クリックし、コンテキスト メニューの \[Properties\] をクリックします。  
  
4.  \[HTTP Headers\] タブをクリックし、\[Enable Content Expiration\] チェック ボックスをオンにします。  
  
5.  コンテンツが 1 分後に期限切れになるように設定します。  
  
<a name="register_mime_types"></a>   
## MIME タイプとファイル拡張子を登録する  
 クライアント システムのブラウザーで適切なハンドラーを読み込めるように、いくつかの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要があります。  次のタイプを追加する必要があります。  
  
|拡張子|MIME タイプ|  
|---------|--------------|  
|.manifest|application\/manifest|  
|xaml|application\/xaml\+xml|  
|.application|application\/x\-ms\-application|  
|xbap|application\/x\-ms\-xbap|  
|.deploy|application\/octet\-stream|  
|xps|application\/vnd.ms\-xpsdocument|  
  
> [!NOTE]
>  クライアント システムに、[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要はありません。  これらは、[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] のインストール時に自動的に登録されます。  
  
 次の [!INCLUDE[TLA#tla_visualbscrpt](../../../../includes/tlasharptla-visualbscrpt-md.md)] のサンプルでは、必要な [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプが [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] に自動的に追加されます。  スクリプトを使用するには、サーバー上の .vbs ファイルにこのコードをコピーします。  コピーしたら、コマンド ラインから、または [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)]でこのファイルをダブルクリックしてスクリプトを実行します。  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  このスクリプトを複数回実行すると、複数の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] マップ エントリが [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに作成されます。  
  
 このスクリプトを実行しても、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] から追加の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを参照できない場合があります。  しかし、これらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに追加されています。  次のスクリプトは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベース内のすべての [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを表示します。  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 スクリプトを `.vbs` ファイルとして保存し \(たとえば、`DiscoverIISMimeTypes.vbs`\)、次のコマンドを使用して、コマンド ラインからこれを実行します。  
  
 `cscript DiscoverIISMimeTypes.vbs`