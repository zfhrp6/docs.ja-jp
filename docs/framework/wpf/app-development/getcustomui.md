---
title: "GetCustomUI | Microsoft Docs"
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
  - "カスタム エラー メッセージ [WPF]"
  - "GetCustomUI メソッド"
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetCustomUI
実装されている場合、ホストから進行状況とエラーのカスタム メッセージを取得するために PresentationHost.exe によって呼び出されます。  
  
## 構文  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### パラメーター  
 `pwzProgressAssemblyName`  
  
 \[out\] ホストから提供される、進行状況のユーザー インターフェイスを格納するアセンブリへのポインター。  
  
 `pwzProgressClassName`  
  
 \[out\] ホストから提供される、進行状況のユーザー インターフェイスのクラス名。<xref:System.Windows.Controls.Page> を持つ [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ファイルは、このクラスのトップ レベルの要素にすることをお勧めします。  このクラスは、`pwzProgressAssemblyName` で指定されたアセンブリにあります。  
  
 `pwzErrorAssemblyName`  
  
 \[out\] ホストから提供される、エラーのユーザー インターフェイスを格納するアセンブリへのポインター。  
  
 `pwzErrorClassName`  
  
 \[out\] ホストから提供される、エラーのユーザー インターフェイスのクラス名。<xref:System.Windows.Controls.Page> を持つ XAML ファイルは、このクラスのトップ レベルの要素にすることをお勧めします。  このクラスは、`pwzErrorAssemblyName` で指定されたアセンブリにあります。  
  
## プロパティ値\/戻り値  
 HRESULT : 無視されます。  
  
## 解説  
 ホスト アプリケーションは、PresentationHost.exe の既定のユーザー インターフェイスが準拠できない特定のテーマを持つ場合があります。  このような場合は、ホスト アプリケーションに [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) を実装して、PresentationHost.exe に進行状況とエラーのユーザー インターフェイスを返すことができます。  PresentationHost.exe は常に、既定のユーザー インターフェイスを使用する前に [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) を呼び出します。  
  
 この関数は、PresentationHost の初期化中に 1 回呼び出されます。  
  
## 参照  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)