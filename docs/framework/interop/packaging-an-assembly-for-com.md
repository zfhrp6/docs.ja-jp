---
title: "COM 用のアセンブリのパッケージ化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 149d0c2595844c5b71767e2ea3ee5b0c6002c080
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-an-assembly-for-com"></a>COM 用のアセンブリのパッケージ化
COM 開発者がアプリケーションに組み込むときに役立つ、マネージ型に関する情報を次に示します。  
  
-   COM アプリケーションで使用できる型の一覧  
  
     マネージ型には、COM から参照できない型、参照可能だが作成できない型、および参照と作成の両方が可能な型があります。 アセンブリは、参照できない型、参照できる型、作成できない型、作成できる型を任意に組み合わせて構成できます。 完全を期すために、COM に公開するアセンブリ内の型を識別する必要があります。特に COM に公開するアセンブリ内の型が .NET Framework に公開されている型のサブセットである場合に型の識別が必要になります。  
  
     追加情報については、「[相互運用のための .NET 型の要件](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)」を参照してください。  
  
-   バージョン管理に関する注意事項  
  
     クラス インターフェイス (COM 相互運用機能により生成されたインターフェイス) を実装したマネージ クラスには、バージョン管理に関する制約が生じる場合があります。  
  
     クラス インターフェイスの使用に関するガイドラインについては、「[クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)」を参照してください。  
  
-   配置に関する注意事項  
  
     発行者により署名された厳密な名前のアセンブリは、グローバル アセンブリ キャッシュにインストールできます。 署名のないアセンブリは、プライベート アセンブリとしてユーザーのコンピューターにインストールする必要があります。  
  
     詳細については、「[アセンブリのセキュリティに関する考慮事項](../../../docs/framework/app-domains/assembly-security-considerations.md)」を参照してください。  
  
-   タイプ ライブラリのインクルード  
  
     大部分の型は、COM アプリケーションで処理されるときにタイプ ライブラリが必要です。 タイプ ライブラリの生成は、自分で行うことも、COM 開発者に任せることもできます。 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、タイプ ライブラリを生成するために次のオプションが用意されています。  
  
    -   [タイプ ライブラリ エクスポーター](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter クラス](#cpconpackagingassemblyforcomanchor2)  
  
    -   [アセンブリ登録ツール](#cpconpackagingassemblyforcomanchor3)  
  
    -   [.NET サービス インストール ツール](#cpconpackagingassemblyforcomanchor4)  
  
     どの機構を選択した場合でも、提供するアセンブリ内で定義されたパブリック型だけが、生成されるタイプ ライブラリに含まれます。  
  
     タイプ ライブラリは、個別のファイルとしてパッケージ化することも、.NET ベースのアプリケーションに Win32 リソースとして埋め込むこともできます。 Microsoft Visual Basic 6.0 ではこの作業は自動的に実行されますが、[!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] を使用する場合は、手動でタイプ ライブラリを埋め込む必要があります。 手順については、「[How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)」(方法: タイプ ライブラリを Win32 リソースとして .NET ベースのアプリケーションに埋め込む) を参照してください。  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>タイプ ライブラリ エクスポーター  
 [タイプ ライブラリ エクスポーター (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) は、アセンブリに含まれているクラスおよびインターフェイスを COM タイプ ライブラリに変換するコマンド ライン ツールです。 クラスの型情報が利用可能になると、COM クライアントは .NET クラスのインスタンスを生成し、COM オブジェクトの場合と同じ方法でインスタンスのメソッドを呼び出すことができます。 Tlbexp.exe により、一度に 1 つのアセンブリ全体が変換されます。 Tlbexp.exe を使用しても、アセンブリで定義されている型のサブセットに関する型情報は生成できません。  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>TypeLibConverter クラス  
 **System.Runtime.Interop** 名前空間にある <xref:System.Runtime.InteropServices.TypeLibConverter> クラスは、アセンブリに含まれているクラスおよびインターフェイスを COM タイプ ライブラリに変換します。 この API は、前のセクションで説明したタイプ ライブラリ エクスポーターと同じ型情報を生成します。  
  
 **TypeLibConverter クラス**は、<xref:System.Runtime.InteropServices.ITypeLibConverter> を実装しています。  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>アセンブリ登録ツール  
 [アセンブリ登録ツール (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) は、**/tlb:** オプションを適用すると、タイプ ライブラリを生成および登録できます。 COM クライアントでは、タイプ ライブラリを Windows のレジストリにインストールする必要があります。 このオプションを適用しない場合、Regasm.exe はアセンブリの型だけを登録し、タイプ ライブラリは登録しません。 アセンブリの型を登録することと、タイプ ライブラリを登録することは、まったく別の作業です。  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>.NET サービス インストール ツール  
 [.NET サービス インストール ツール (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) は、Windows 2000 コンポーネント サービスにマネージ クラスを追加したり、1 つのツール内の複数のタスクを統合したりします。 Regsvcs.exe は、アセンブリの読み込みおよび登録だけでなく、タイプ ライブラリの生成、登録、および既存の COM+ 1.0 アプリケーションへのインストールができます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [要件 (相互運用のための .NET 型の)](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [クラス インターフェイスの概要](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [アセンブリのセキュリティに関する考慮事項](../../../docs/framework/app-domains/assembly-security-considerations.md)  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [COM へのアセンブリの登録](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [方法: タイプ ライブラリを Win32 リソースとしてアプリケーションに埋め込む](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)
