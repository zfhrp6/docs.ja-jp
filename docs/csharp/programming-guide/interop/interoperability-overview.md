---
title: 相互運用性の概要 (C# プログラミング ガイド)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 51a92f89415fd3750d8d2e1880be0d9c2867600d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="interoperability-overview-c-programming-guide"></a>相互運用性の概要 (C# プログラミング ガイド)
C# マネージ コードとアンマネージ コード間で相互運用を可能にする方法について説明します。  
  
## <a name="platform-invoke"></a>プラットフォーム呼び出し  
 "*プラットフォーム呼び出し*" とは、Microsoft Win32 API にあるような、ダイナミックリンク ライブラリ (DLL) で実装されているアンマネージ関数をマネージ コードで呼び出すことを可能にするサービスです。 これはエクスポートされた関数を見つけて呼び出し、必要に応じて相互運用の境界を越えて、その引数 (整数、文字列、配列、構造体、その他) をマーシャリングします。  
  
 詳細については、「[アンマネージ DLL 関数の処理](../../../framework/interop/consuming-unmanaged-dll-functions.md)」と「[方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)」を参照してください。  
  
> [!NOTE]
>  [共通言語ランタイム](../../../standard/clr.md) (CLR) が、システム リソースへのアクセスを管理します。 CLR の外部のアンマネージ コードを呼び出すと、このセキュリティ メカニズムがバイパスされるため、セキュリティ リスクが生じます。 たとえば、アンマネージ コードがアンマネージ コード内のリソースを直接呼び出した場合、CLR のセキュリティ機構がバイパスされます。 詳細については、[.NET Framework セキュリティ](https://technet.microsoft.com/en-us/security/)に関する記事を参照してください。  
  
## <a name="c-interop"></a>C++ Interop  
 It Just Works (IJW) とも呼ばれる C++ interop を使用してネイティブ C++ クラスをラップすると、このクラスを C# またはその他の .NET Framework 言語で作成されたコードで使用できるようになります。 これを行うには、C++ コードを記述して、ネイティブ DLL または COM コンポーネントをラップします。 他の .NET Framework 言語とは異なり、[!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] には相互運用性サポートが備えられています。これにより、マネージ コードとアンマネージ コードは同じアプリケーション内、また同じファイルでも共存できるようになります。 C++ コードは、マネージ アセンブリを生成する **/clr** コンパイラ スイッチを使用して構築できます。 最後に、C# プロジェクトのアセンブリへの参照を追加し、他のマネージ クラスを使用するときと同じように、ラップされたオブジェクトを使用します。  
  
## <a name="exposing-com-components-to-c"></a>C# への COM コンポーネントの公開  
 C# プロジェクトから COM コンポーネントを使用することができます。 一般的な手順は次のとおりです。  
  
1.  使用する COM コンポーネントを探して登録します。 regsvr32.exe を使用して、COM DLL の登録または登録解除を行います。  
  
2.  プロジェクトに、COM コンポーネントまたはタイプ ライブラリへの参照を追加します。  
  
     参照を追加する際、Visual Studio は [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) を使用します。これにより、タイプ ライブラリを入力として取得し、.NET Framework 相互運用アセンブリを出力します。 このアセンブリは、ランタイム呼び出し可能ラッパー (RCW) とも呼ばれ、タイプ ライブラリ内の COM クラスとインターフェイスをラップする、マネージ クラスとインターフェイスを含みます。 Visual Studio は、生成されたアセンブリへの参照をプロジェクトに追加します。  
  
3.  RCW で定義されているクラスのインスタンスを作成します。 これにより、COM オブジェクトのインスタンスが作成されます。  
  
4.  他のマネージ オブジェクトを使用するときと同様に、オブジェクトを使用します。 オブジェクトがガベージ コレクションによって解放されるとき、COM オブジェクトのインスタンスもメモリから解放されます。  
  
 詳細については、「[.NET Framework への COM コンポーネントの公開](../../../../docs/framework/interop/exposing-com-components.md)」を参照してください。  
  
## <a name="exposing-c-to-com"></a>COM への C# の公開  
 COM クライアントは、適切に公開されている C# 型を使用できます。 C# 型を公開する基本的な手順は次のとおりです。  
  
1.  C# プロジェクトに相互運用属性を追加します。  
  
     アセンブリ COM は、Visual C# プロジェクト プロパティを変更することで参照できるようになります。 詳細については、「[[アセンブリ情報] ダイアログ ボックス](/visualstudio/ide/reference/assembly-information-dialog-box)」を参照してください。  
  
2.  COM タイプ ライブラリを生成し、COM の使用状況に登録します。  
  
     Visual C# プロジェクト プロパティを変更して、C# アセンブリが COM 相互運用に自動的に登録されるようにできます。 Visual Studio は `/tlb` コマンド ライン スイッチを使用して [Regasm.exe (アセンブリ登録ツール)](../../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) を使用します。これにより、マネージ アセンブリが入力として取得され、タイプ ライブラリを生成できます。 タイプ ライブラリは、アセンブリ内の `public` 型を記述し、レジストリ エントリを追加することで、COM クライアントがマネージ クラスを作成できるようにします。  
  
 詳細については、「[COM への .NET Framework コンポーネントの公開](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)」と「[COM クラスの例](../../../csharp/programming-guide/interop/example-com-class.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [相互運用パフォーマンスの向上](https://msdn.microsoft.com/library/ms998551.aspx)  
 [COM と .NET の相互運用性の概要](https://msdn.microsoft.com/library/office/bb610378.aspx)  
 [COM 相互運用の概要 (Visual Basic)](../../../../docs/visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 [マネージ コードとアンマネージ コード間でのマーシャリング](../../../../docs/framework/interop/interop-marshaling.md)  
 [アンマネージ コードとの相互運用](../../../../docs/framework/interop/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
