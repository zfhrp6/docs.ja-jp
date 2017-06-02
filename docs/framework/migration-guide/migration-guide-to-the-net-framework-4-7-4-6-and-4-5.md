---
title: ".NET Framework 4.6 および 4.5 移行ガイド  | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework、移行する先 (アプリケーションを)"
  - "移行、.NET Framework"
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
caps.latest.revision: 56
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# .NET Framework 4.6 および 4.5 移行ガイド 
アプリを旧バージョンの .NET Framework を使用して作成した場合、通常は .NET Framework 4.5、4.5.1、または 4.6 に簡単にアップグレードできます。 Visual Studio でプロジェクトを開きます。 プロジェクトが旧バージョンで作成されている場合は、**\[Project Compatibility\]**\(プロジェクト互換性\) ダイアログ ボックスが自動的に開きます。 Visual Studio 2013 におけるプロジェクトのアップグレードの詳細については、「[方法: 旧バージョンの Visual Studio で作成されたプロジェクトをアップグレードする](http://msdn.microsoft.com/library/vstudio/ms185327\(v=vs.100\).aspx)」と「[Visual Studio プロジェクトの移植、移行、およびアップグレード](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)」を参照してください。  
  
 ただし、.NET Framework で行われたいくつかの変更により、コードを変更する必要があります。 .NET Framework 4.5、そのポイント リリース、または .NET Framework 4.6 の新しい機能を利用することもできます。 .NET Framework の新しいバージョンに対応するためのアプリに対するこの種の変更は、一般に*移行*と呼ばれます。 アプリを移行する必要がない場合、アプリは再コンパイルなしで .NET Framework 4.5 またはそれ以降のバージョンで実行できます。  
  
## 移行のためのリソース  
 アプリを .NET Framework の旧バージョンから Version 4.5、4.5.1、または 4.5.2 に移行する前に、次のドキュメントを確認します。  
  
-   .NET Framework の各バージョンの基になる CLR バージョンを理解し、アプリを正しく対象とするためのガイドラインを確認するには、「[バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください。  
  
-   ランタイムおよびアプリに影響を与える可能性のある変更の再ターゲットについて、およびそれらの処理方法を確認するには、「[アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)」を確認します。  
  
-   「[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)」を参照して、廃止された型またはメンバーがコードに含まれていないか調べ、また、推奨される代替の型またはメンバーを確認します。  
  
-   アプリに追加できる可能性のある新機能の説明については、「[新機能](../../../docs/framework/whats-new/index.md)」を参照してください。  
  
## 参照  
 [4.5.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [.NET Framework 1.1 からの移行](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [バージョンの互換性](../../../docs/framework/migration-guide/version-compatibility.md)   
 [バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [方法 : .NET Framework 4 または 4.5 をサポートするアプリケーションを構成する](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)   
 [新機能](../../../docs/framework/whats-new/index.md)   
 [クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [.NET Framework のバージョンとアセンブリ情報](http://go.microsoft.com/fwlink/?LinkId=201701)   
 [Microsoft .NET Framework のサポート ライフサイクル ポリシー](http://go.microsoft.com/fwlink/?LinkId=196607)