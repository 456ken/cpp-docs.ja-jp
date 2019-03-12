---
title: ファイル変換定数
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: ef9b986753de05c45b3071e55f9b163fa5a6a7da
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743323"
---
# <a name="file-translation-constants"></a>ファイル変換定数

## <a name="syntax"></a>構文

```
#include <stdio.h>
```

## <a name="remarks"></a>解説

これらの定数は、変換モードを指定します (**"b"** または **"t"**)。 このモードは、アクセスの種類 (**"r"**、**"w"**、**"a"**、**"r+"**、**"w+"**、**"a+"**) を指定する文字列に含まれます。

変換モードは次のとおりです。

- **t**

   テキスト (変換) モードで開きます。 このモードでは、復帰と改行 (CR-LF) の組み合わせは入力時に 1 つの改行 (LF) 文字に変換され、LF 文字は出力時に CR-LF の組み合わせに変換されます。 また、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 読み取り用または読み取り/書き込み用にファイルを開いた場合、`fopen` はファイルの終端に Ctrl + Z があるかどうかを確認し、それを削除できる場合は削除します。 この処理が行われる理由は、CTRL+Z で終わるファイルの中身を `fseek` 関数および `ftell` 関数で移動するとき、ファイル末尾付近で `fseek` が正しく動作しないことがあるためです。

   > [!NOTE]
   > **t** のオプションは、`fopen` と `freopen` の ANSI 標準の一部ではありません。 これは Microsoft 拡張機能です。ANSI 互換が必要な場合は使用しないでください。

- **b**

   バイナリ (無変換) モードで開きます。 上の変換は行われません。

**t** または **b** を *mode* に指定しない場合、変換モードは既定のモード変数 [_fmode](../c-runtime-library/fmode.md) によって定義されます。 テキスト モードとバイナリ モードの使用の詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../c-runtime-library/text-and-binary-mode-file-i-o.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
