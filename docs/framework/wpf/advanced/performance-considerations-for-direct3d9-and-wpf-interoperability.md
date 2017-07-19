---
title: "Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項 | Microsoft Docs"
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
  - "Direct3D9 [WPF 相互運用性], パフォーマンス"
  - "WPF, Direct3D9 相互運用パフォーマンス"
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項
<xref:System.Windows.Interop.D3DImage> クラスを使用して、Direct3D9 コンテンツをホストできます。  Direct3D9 コンテンツをホストすると、アプリケーションのパフォーマンスに影響することがあります。  このトピックでは、Windows Presentation Foundation \(WPF\) アプリケーションで Direct3D9 コンテンツをホストする場合に、パフォーマンスを最適化するベスト プラクティスについて説明します。  これらのベスト プラクティスでは、<xref:System.Windows.Interop.D3DImage> の使用方法と、Windows Vista、Windows XP、およびマルチモニター ディスプレイを使用する場合のベスト プラクティスを紹介します。  
  
> [!NOTE]
>  これらのベスト プラクティスを示すコード例については、「[WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)」を参照してください。  
  
## 最小限の D3DImage の使用  
 <xref:System.Windows.Interop.D3DImage> インスタンスでホストされる Direct3D9 コンテンツは、純粋な Direct3D アプリケーションでホストされる場合よりも表示が遅くなります。  サーフェイスのコピーおよびコマンド バッファーのフラッシュに時間がかかることがあります。  <xref:System.Windows.Interop.D3DImage> インスタンスの数が増えると、フラッシュの回数が多くなり、パフォーマンスが低下します。  したがって、<xref:System.Windows.Interop.D3DImage> の使用を最小限にする必要があります。  
  
## Windows Vista のベスト プラクティス  
 ディスプレイが Windows Display Driver Model \(WDDM\) を使用するように構成されている Windows Vista で最大限のパフォーマンスを得るには、Direct3D9 サーフェイスを `IDirect3DDevice9Ex` デバイス上に作成します。  これにより、サーフェイスを共有できるようになります。  ビデオカードは、Windows Vista の `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` および `D3DCAPS2_CANSHARERESOURCE` というドライバーの機能をサポートしている必要があります。  その他の設定では、サーフェイスがソフトウェアを通してコピーされ、パフォーマンスが大幅に低下します。  
  
> [!NOTE]
>  Windows Vista に、Windows XP Display Driver Model \(XDDM\) を使用するように構成されているディスプレイがある場合は、設定にかかわらず、サーフェイスが常にソフトウェアを通じてコピーされます。  適切な設定とビデオ カードがあれば、サーフェイスのコピーはハードウェアで実行されるため、WDDM を使用するときに Windows Vista のパフォーマンスが向上します。  
  
## Windows XP のベスト プラクティス  
 Windows XP Display Driver Model \(XDDM\) を使用する Windows XP でパフォーマンスを最適にするために、`IDirect3DSurface9::GetDC` メソッドが呼び出されたときに正しく動作するロック可能なサーフェイスを作成します。  内部的に、`BitBlt` メソッドはハードウェアのデバイス間でサーフェイスを転送します。  `GetDC` メソッドは、常に XRGB サーフェイス上で動作します。  ただし、クライアント コンピューターで Windows XP SP3 または SP2 が実行されており、レイヤード ウィンドウ機能の修正プログラムも適用されている場合、このメソッドは ARGB サーフェイス上でのみ動作します。  ビデオ カードは、`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` ドライバー機能をサポートする必要があります。  
  
 16 ビット デスクトップ表示深度を使用すると、パフォーマンスが大幅に低下することがあります。  32 ビット デスクトップをお勧めします。  
  
 Windows Vista および Windows XP で開発している場合は、Windows XP 上でパフォーマンスをテストします。  Windows XP のビデオ メモリが不足することは問題です。  また、Windows XP 上の <xref:System.Windows.Interop.D3DImage> では、余分なビデオ メモリ コピーが必要なため、Windows Vista WDDM よりも多くのビデオ メモリと帯域幅を使用します。  したがって、同じビデオ ハードウェアの場合は Windows Vista よりも Windows XP の方がパフォーマンスが低いと予想されます。  
  
> [!NOTE]
>  XDDM は、Windows XP と Windows Vista の両方で使用できますが、WDDM は Windows Vista でのみ使用できます。  
  
## 一般的なベスト プラクティス  
 デバイスを作成する場合は、`D3DCREATE_MULTITHREADED` 作成フラグを使用します。  これにより、パフォーマンスが低下しますが、WPF レンダリング システムは、別のスレッドからこのデバイスに対してメソッドを呼び出します。  ロック プロトコルに正しく従い、2 つのスレッドがデバイスに同時にアクセスしないようにしてください。  
  
 レンダリングが WPF マネージ スレッドで実行される場合は、`D3DCREATE_FPU_PRESERVE` 作成フラグを使用してデバイスを作成することを強くお勧めします。  この設定がないと、D3D レンダリングによって、WPF の倍精度演算の精度が低下し、レンダリングの問題が発生することがあります。  
  
 ハードウェア サポートがない状態で非 pow2 サーフェイスを並べて表示するのでない場合、または、<xref:System.Windows.Interop.D3DImage> を含む <xref:System.Windows.Media.DrawingBrush> か <xref:System.Windows.Media.VisualBrush> を並べて表示する場合は、<xref:System.Windows.Interop.D3DImage> を並べて表示するのが高速です。  
  
## マルチモニター ディスプレイのベスト プラクティス  
 複数のモニターがあるコンピューターを使用している場合は、前に説明したベスト プラクティスに従う必要があります。  マルチモニター構成に関する追加のパフォーマンス考慮事項もいくつかあります。  
  
 バック バッファーを作成する場合は、特定のデバイスおよびアダプターに作成されますが、WPF は任意のアダプターのフロント バッファーを表示する場合があります。  アダプター間でコピーしてフロント バッファーを更新すると、非常にコストが高くなる可能性があります。  複数のビデオ カードと `IDirect3DDevice9Ex` デバイスと共に WDDM を使用するように構成されている Windows Vista では、フロント バッファーが別のアダプターにあっても、同じビデオ カードである場合は、パフォーマンスの低下はありません。  ただし、Windows XP と複数のビデオ カードのある XDDM では、フロント バッファーがバック バッファーとは異なるアダプターに表示される場合にパフォーマンスが大幅に低下します。  詳細については、「[WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)」を参照してください。  
  
## パフォーマンスの概要  
 次の表に、オペレーティング システムの機能、ピクセル形式、およびサーフェイスのロック可能性としてのフロント バッファー更新のパフォーマンスを示します。  フロント バッファーとバック バッファーは、同じアダプター上にあることが前提です。  アダプター構成に応じて、ハードウェア更新は、一般にソフトウェア更新よりもはるかに高速です。  
  
|サーフェイスのピクセル形式|Windows Vista、WDDM、および 9Ex|その他の Windows Vista 構成|修正プログラムを適用した Windows XP SP3 または SP2|Windows XP SP2|  
|-------------------|--------------------------------|---------------------------|-----------------------------------------|--------------------|  
|D3DFMT\_X8R8G8B8 \(ロック不能\)|**ハードウェアのアップデート**|ソフトウェアのアップデート|ソフトウェアのアップデート|ソフトウェアのアップデート|  
|D3DFMT\_X8R8G8B8 \(ロック可能\)|**ハードウェアのアップデート**|ソフトウェアのアップデート|**ハードウェアのアップデート**|**ハードウェアのアップデート**|  
|D3DFMT\_A8R8G8B8 \(ロック不能\)|**ハードウェアのアップデート**|ソフトウェアのアップデート|ソフトウェアのアップデート|ソフトウェアのアップデート|  
|D3DFMT\_A8R8G8B8 \(ロック可能\)|**ハードウェアのアップデート**|ソフトウェアのアップデート|**ハードウェアのアップデート**|ソフトウェアのアップデート|  
  
## 参照  
 <xref:System.Windows.Interop.D3DImage>   
 [WPF と Direct3D9 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)   
 [チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)   
 [チュートリアル : WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)