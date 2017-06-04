---
title: "イントラネット アプリケーションの完全信頼での実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "完全信頼, 実行 (イントラネット アプリケーションを)"
  - "イントラネット アプリケーション, 実行 (完全信頼で)"
  - "実行 (イントラネット アプリケーションを完全信頼で)"
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# イントラネット アプリケーションの完全信頼での実行
.NET Framework Version 3.5 Service Pack 1 \(SP1\) 以降では、アプリケーションとライブラリ アセンブリを、完全に信頼されているアセンブリとしてネットワーク共有から実行できるようになりました。  イントラネットの共有から読み込まれるアセンブリには、<xref:System.Security.SecurityZone> ゾーンの証拠が自動的に追加されます。  この証拠はアセンブリに対し、コンピューター上にあるアセンブリと同じ許可セット \(通常は完全信頼\) を付与します。  この機能は、ホスト上で実行するように設計されている ClickOnce アプリケーションには適用されません。  
  
## ライブラリ アセンブリの規則  
 ネットワーク共有から実行可能ファイルによって読み込まれるアセンブリには、次の規則が適用されます。  
  
-   ライブラリ アセンブリは、実行可能なアセンブリと同じフォルダーに存在する必要があります。  サブフォルダーにあるアセンブリや、別のパスで参照されるアセンブリには、完全信頼の許可セットは付与されません。  
  
-   実行可能ファイルがアセンブリを遅延読み込みする場合、その実行可能ファイルの起動に使用したのと同じパスを使用する必要があります。  たとえば、共有の\\\\の*network\-computer*の\\*share* がドライブ文字にマップされ、実行可能ファイルを実行すると、そのパスから使用して実行可能ファイルによって読み込まれるアセンブリは、ネットワーク パス、完全信頼が付与されません。  <xref:System.Security.SecurityZone> ゾーンでアセンブリを遅延読み込みするには、実行可能ファイルがドライブ文字のあるパスを使用している必要があります。  
  
## 以前のイントラネット ポリシーの復元  
 .NET Framework の以前のバージョンでは、共有アセンブリには <xref:System.Security.SecurityZone> ゾーンの証拠が付与されていました。  共有上のアセンブリに完全な信頼を付与するには、コード アクセス セキュリティ ポリシーを指定する必要がありました。  
  
 この新しい動作は、イントラネット アセンブリの既定の動作です。  コンピューターのすべてのアプリケーションに適用されるレジストリ キー値を設定することで、以前の <xref:System.Security.SecurityZone> 証拠が使用される動作に戻すことができます。  この手順は、32 ビット コンピューターと 64 ビット コンピューターで異なります。  
  
-   32 ビット コンピューターでは、システム レジストリの HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework キーの下にサブキーを作成します。  キーの名前は LegacyMyComputerZone とし、DWORD 値 1 を設定します。  
  
-   64 ビット コンピューターでは、システム レジストリの HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework キーの下にサブキーを作成します。  キーの名前は LegacyMyComputerZone とし、DWORD 値 1 を設定します。  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework キー下に同じサブキーを作成します。  
  
## 参照  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)