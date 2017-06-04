---
title: "アセンブリを使用したプログラミング | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], プログラミング"
  - "プログラミング (アセンブリの)"
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# アセンブリを使用したプログラミング
アセンブリは .NET Framework のビルド ブロックであり、配置、バージョン管理、再利用、アクティブ化のスコープの指定、およびセキュリティ アクセス許可の基本単位となります。  共通言語ランタイムは、型の実装に関して必要な情報をアセンブリから取得します。  アセンブリは、相互に連携して 1 つの論理的な機能単位を形成するように構築された型やリソースの集合です。  共通言語ランタイムにとって、型はアセンブリのコンテキストの外部には存在しません。  
  
 このセクションでは、モジュールの作成、モジュールからのアセンブリの作成、キー ペアの作成、厳密な名前でのアセンブリへの署名、およびグローバル アセンブリ キャッシュへのアセンブリのインストールについて説明します。  また、このセクションでは、[MSIL 逆アセンブラー \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用したアセンブリ マニフェスト情報の表示方法についても説明します。  
  
> [!NOTE]
>  .NET Framework Version 2.0 以降では、現在読み込まれているランタイムよりもバージョン番号が新しい .NET Framework のバージョンでコンパイルされたアセンブリを、ランタイムが読み込まないようになりました。  これに該当するのは、バージョン番号のメジャー部分とマイナー部分を組み合わせた番号です。  
  
## このセクションの内容  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)  
 シングルファイル アセンブリとマルチファイル アセンブリの概要を説明します。  
  
 [アセンブリ名](../../../docs/framework/app-domains/assembly-names.md)  
 アセンブリの名前付けの概要を説明します。  
  
 [方法 : アセンブリの完全修飾名を特定する](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 アセンブリの完全修飾名を決定する方法を説明します。  
  
 [イントラネット アプリケーションの完全信頼での実行](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 イントラネット共有で完全に信頼されているアセンブリのレガシ セキュリティ ポリシーを指定する方法を説明します。  
  
 [アセンブリの場所](../../../docs/framework/app-domains/assembly-location.md)  
 アセンブリを配置する場所の概要を説明します。  
  
 [方法: シングルファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 シングルファイル アセンブリの作成方法を説明します。  
  
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)  
 マルチファイル アセンブリを作成する理由を説明します。  
  
 [方法 : マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 マルチファイル アセンブリの作成方法を説明します。  
  
 [アセンブリ属性の設定](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 アセンブリ属性とその設定方法を説明します。  
  
 [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 厳密な名前を使用してアセンブリに署名する方法とその理由について、具体的な手順を交えて説明します。  
  
 [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 アセンブリに遅延署名する方法を説明します。  
  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 グローバル アセンブリ キャッシュにアセンブリを追加する方法とその理由について、具体的な手順を交えて説明します。  
  
 [方法 : アセンブリの内容を表示する](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 MSIL 逆アセンブラー \(Ildasm.exe\) を使用したアセンブリ内容の表示方法を説明します。  
  
 [共通言語ランタイムでの型の転送](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 型の転送を使用して、既存のアプリケーションを壊すことなく型を別のアセンブリに移動させる方法について説明します。  
  
## 関連項目  
 <xref:System.Reflection.Assembly>  
 アセンブリを表す .NET Framework クラス。  
  
## 関連項目  
 [方法 : アセンブリから型およびメンバーの情報を取得する](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 アセンブリから型情報などの情報をプログラムによって取得する方法を説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 共通言語ランタイムアセンブリの概念的な概要を説明します。  
  
 [アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)  
 アセンブリのバインディングと、<xref:System.Reflection.AssemblyVersionAttribute> 属性および <xref:System.Reflection.AssemblyInformationalVersionAttribute> 属性について概要を説明します。  
  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 バインディング要求を満たすために使用するアセンブリを、ランタイムが決定する方法を説明します。  
  
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使って、アセンブリに関する情報を取得する方法を説明します。