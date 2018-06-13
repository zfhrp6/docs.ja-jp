---
title: Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 52085579c2a432e7db1ebec096a931e0d51718f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549205"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
使用して Direct3D9 コンテンツをホストすることができます、<xref:System.Windows.Interop.D3DImage>クラスです。 Direct3D9 コンテンツをホストするいると、アプリケーションのパフォーマンスに影響する可能性です。 このトピックでは、Windows Presentation Foundation (WPF) アプリケーションで Direct3D9 コンテンツをホストする場合にパフォーマンスを最適化するために、ベスト プラクティスについて説明します。 これらのベスト プラクティスには、使用する方法が含まれます。<xref:System.Windows.Interop.D3DImage>およびベスト プラクティスの Windows Vista、Windows XP を使用していると、複数のモニターに表示されます。  
  
> [!NOTE]
>  これらのベスト プラクティスを説明するコード例では、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)です。  
  
## <a name="use-d3dimage-sparingly"></a>D3DImage を多用しません。  
 ホストされている Direct3D9 コンテンツ、<xref:System.Windows.Interop.D3DImage>インスタンスが、純粋な Direct3D アプリケーションと同様に高速として表示されません。 サーフェイスのコピーとコマンド バッファーのフラッシュは、コストの高い操作を指定できます。 数として<xref:System.Windows.Interop.D3DImage>インスタンスが増えると、複数のフラッシュが発生し、パフォーマンスが低下します。 したがって、使用する必要があります<xref:System.Windows.Interop.D3DImage>限定的に使用します。  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista でのベスト プラクティス  
 Windows 表示 Driver Model (WDDM) を使用するように構成するディスプレイと Windows Vista の最適なパフォーマンスは、上、Direct3D9 画面を作成、`IDirect3DDevice9Ex`デバイス。 これにより、画面を共有できます。 ビデオ カードをサポートする必要があります、`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`と`D3DCAPS2_CANSHARERESOURCE`Windows Vista でのドライバーの機能です。 その他の設定には、パフォーマンスが大幅に低下するためのソフトウェアをコピーする画面が発生します。  
  
> [!NOTE]
>  Windows Vista では、Windows XP 表示ドライバー モデル (XDDM) を使用するように構成の表示が、設定に関係なく、ソフトウェアを介して、画面は常にコピーします。 画面のコピーは、ハードウェアで実行されるため、WDDM を使用する場合の適切な設定とビデオ カードでは、パフォーマンスを向上させる Windows Vista 上に表示されます。  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP 上のベスト プラクティス  
 最適なパフォーマンスを Windows xp では、Windows XP ディスプレイ ドライバー モデル (XDDM) を使用が正しく動作するためのロック可能なサーフェイスの作成時に、`IDirect3DSurface9::GetDC`メソッドが呼び出されます。 内部的には、`BitBlt`メソッドは、ハードウェア デバイス間で、画面を転送します。 `GetDC`メソッドは常に XRGB サーフェスで動作します。 ただし、クライアント コンピューターは、SP3 または SP2、Windows XP を実行している場合、および、クライアントは階層化ウィンドウの機能の修正プログラムもある場合は、このメソッドはのみ ARGB 画面に機能します。 ビデオ カードをサポートする必要があります、`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`ドライバー機能します。  
  
 デスクトップの表示を 16 ビットの深さは、パフォーマンスを大幅に削減できます。 32 ビットのデスクトップをお勧めします。  
  
 Windows Vista および Windows XP 開発している場合は、Windows XP 上のパフォーマンスをテストします。 Windows XP でのビデオ メモリ不足は問題です。 さらに、 <xref:System.Windows.Interop.D3DImage> Windows XP で複数のビデオ メモリと必要な余分なビデオ メモリのコピーのための Windows Vista WDDM よりも帯域幅を使用します。 したがって、同じビデオ ハードウェアが Windows Vista でよりも、Windows XP の低いパフォーマンスを期待できます。  
  
> [!NOTE]
>  XDDM は Windows XP および Windows Vista; の両方で使用できます。ただし、WDDM は Windows Vista でのみ使用できます。  
  
## <a name="general-best-practices"></a>一般的なベスト プラクティス  
 デバイスを作成するときに使用して、`D3DCREATE_MULTITHREADED`作成フラグ。 この、パフォーマンスが低下しますが、WPF レンダリング システムは、別のスレッドからこのデバイス上でメソッドを呼び出します。 必ずロック プロトコルの後ろに正しくない 2 つのスレッドがデバイスを同時にアクセスできるようにします。  
  
 レンダリングが管理されている WPF のスレッドで実行される場合を使用してデバイスを作成することを強くお勧め、`D3DCREATE_FPU_PRESERVE`作成フラグ。 この設定がない、D3D 表示モードの WPF の倍精度演算の精度が低下し、レンダリングの問題が発生することができます。  
  
 並べて表示、<xref:System.Windows.Interop.D3DImage>を並べて表示する場合、またはハードウェア サポートのない非 pow2 サーフェスを並べて表示する場合を除き、高速では、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>を格納している、<xref:System.Windows.Interop.D3DImage>です。  
  
## <a name="best-practices-for-multi-monitor-displays"></a>マルチ モニター表示のベスト プラクティス  
 複数のモニターを持つコンピューターを使用している場合は、既に説明したベスト プラクティスに従う必要があります。 マルチ モニターの構成のいくつか追加のパフォーマンスに関する考慮事項もあります。  
  
 バック バッファーを作成するときに、特定のデバイスと、アダプター上に作成されますが、WPF は、アダプターの前面のバッファーを表示することがあります。 フロントのバッファーを更新するアダプター間でコピーと、非常に高価なことができます。 WDDM の複数のビデオ カードと共に使用するように構成は、Windows Vista で、`IDirect3DDevice9Ex`デバイス、前面のバッファーが別のアダプターが、引き続き同じビデオ カード上にある場合は、パフォーマンスの低下はありません。 ただし、Windows XP および複数のビデオ カードで XDDM では、大幅なパフォーマンスの低下フロント バッファーは、バック バッファーとは異なるアダプターに表示されるときにします。 詳細については、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)です。  
  
## <a name="performance-summary"></a>パフォーマンスの概要  
 次の表では、オペレーティング システム、ピクセル形式、およびサーフェイスのロック可能性の関数としてフロント バッファー更新プログラムのパフォーマンスを表示します。 バッファーのフロントとバック バッファーは、同じアダプター上にあると見なされます。 アダプターの構成に応じて、ハードウェアの更新プログラムは通常、ソフトウェア更新プログラムよりもはるかに高速です。  
  
|画面のピクセル形式|Windows Vista、WDDM および 9Ex|その他の Windows Vista の構成|Windows XP SP3 または修正プログラムを使用した SP2|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (lockable されません)|**ハードウェアの更新**|ソフトウェアの更新|ソフトウェアの更新|ソフトウェアの更新|  
|D3DFMT_X8R8G8B8 (lockable)|**ハードウェアの更新**|ソフトウェアの更新|**ハードウェアの更新**|**ハードウェアの更新**|  
|(ロックではない) では D3DFMT_A8R8G8B8|**ハードウェアの更新**|ソフトウェアの更新|ソフトウェアの更新|ソフトウェアの更新|  
|(ロック) では D3DFMT_A8R8G8B8|**ハードウェアの更新**|ソフトウェアの更新|**ハードウェアの更新**|ソフトウェアの更新|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Interop.D3DImage>  
 [WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [チュートリアル: WPF でホストするための Direct3D9 コンテンツの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [チュートリアル: WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
