# 概要
  - [説明](#説明)
  - [利用規約](#利用規約)
  - [機能](#機能)
  - [セットアップ](#セットアップ)
  - [使い方](#使い方)
  - [サポート](#サポート)
  - [関連プロジェクト](#関連プロジェクト)
  - [貢献者](#貢献者)

# 説明
`VVVF-Simulator`はPC上でVVVFインバータの音をシミュレートするソフトウェアです。<br>
このプログラムはC# WPFアプリケーション向けです。<br>

# 利用規約
このプログラムのコードは**自由に**使用できます。<br>
このアプリケーションに関するあらゆる行動について、**当方は責任を負いません**。<br>

お願いします:<br>
- このGitHubページのURLを張り付けてください<br>

避けてください:<br>
- このページを参照せずに改変したコードを公開しないでください<br>

# 機能
## VVVF波形音生成
このアプリケーションは模擬されたVVVFインバータの音を`.wav`形式でエクスポートします。<br>
サンプリング周波数は192kHzです。<br>

## 波形動画生成
このアプリケーションはビデオを`.avi`形式でエクスポートします。
![2022-02-14](https://user-images.githubusercontent.com/77259842/153803020-6615bcce-22a6-4839-b919-ea114dc12d03.png)

## 電圧ベクトル動画生成
このアプリケーションはビデオを`.avi`形式でエクスポートします。

## 制御状態動画生成
このアプリケーションは制御状態の値のビデオをエクスポートできます。<br>
ファイルは`.avi`形式です。<br>
![2022-06-11 (1)](https://user-images.githubusercontent.com/77259842/173188884-72a1290a-6d7b-4354-88e4-cecfa5d0d424.png)

## リアルタイムオーディオ生成
リアルタイムでオーディオを生成し、自由に音を聞くことができます。<br>

# セットアップ
PC上でコードをビルドするか、単にexeファイルをダウンロードできます。<br>
## EXEでのセットアップ
[Releases](https://github.com/VvvfGeeks/VVVF-Simulator/releases)に移動し、`VVVF-SIM.zip`をダウンロードしてください。<br>
zipファイルを解凍します。`VVVF-Simulator.exe`が見つかるはずです。<br>

## Visual Studioのソースコードでのセットアップ
まず、Visual Studioをダウンロードします。インストーラーを実行し、インストーラーで.NETデスクトップ開発も選択してください。インストールが完了したらVisual Studioを開き、「リポジトリのクローン」をクリックします。次に、VVVF-SimulatorページのURLをコピーします。
<br>
https://github.com/VvvfGeeks/VVVF-Simulator
<br>
URLを貼り付け、クローンをクリックします。次に「ソリューション 'VVVF-Simulator'」をクリックし、プログラムをコンパイルして実行するための緑の矢印をクリックします。これでウィンドウが開くはずです。
<br>

# 使い方
ファイルを読み込むか保存するには、ファイルをクリックしてそこから行いたい操作を選択します。
<br>
<br>
リアルタイムでサウンドを生成するには、RealTimeタブをクリックします。 "VVVF RealTime"はオーディオを通じて再生される生成されたPWMで、"Train RealTime"は列車の音をシミュレートします。
<br>
<br>
これらの設定の詳細については、それぞれの設定をクリックすると、オーディオバッファサイズを変更したり、制御変数を表示したり、ベクトルヘキサゴンを表示したり、波形を表示したり、リアルタイム編集を有効にしたり、FFTを表示したりすることができます。ただし、これらを有効にするほど、処理能力が必要です。
<br>
<br>
サウンドの作成方法:
<br>
<br>
まず、「Settings」をクリックします。次に、「PWM Level」をクリックします。ここで、サウンドに使用されるPWMレベルの数を選択します。ほとんどの列車は2つのレベルを使用します。
<br>
<br>
次に、「Minimum Frequency」をクリックします。これは、加速とブレーキングのために生成される最低周波数を設定します。制御周波数がこの値よりも低い場合、出力周波数は制御周波数が0よりも大きい限り、この値のままですが、振幅は変化します。最小の出力周

波数を0から開始する場合は、値を0に変更します。
<br>
<br>
次に、「Jerk Control」をクリックします。これらの設定は、出力が完全にオンまたはオフになるまでの時間を変更します。 "Freq Goto"はオンまたはオフになるときに出力周波数が移動する値です。 "Change Rate"はその値に到達するための毎秒のサイクル数です。 "Mascon On"は出力をオンにし、 "Mascon Off"は出力をオフにすることを意味します。これは加速とブレーキングの両方に設定できます。
<br>
<br>
次に、「Accelerate」をクリックします。ここではサウンドの設定を作成します。底部の+をクリックしてサウンドの設定を追加できます。その設定をクリックして-をクリックして削除できます。
<br>
<br>
次に、サウンドをクリックし、「From」の位置は、その設定が始まる出力周波数です。これが最初のものである場合は、最小の出力周波数を設定します。
<br>
<br>
「Basic Setting」の上にあるドロップダウンメニューでPWMのタイプを設定します。Asycはキャリア周波数が出力と同期していないことを意味します。 "P_Wide_3"は広い三つのパルスモードPWMです。 "P_"と書かれている設定は同期PWMモードであり、キャリア周波数は出力の倍数です。 "CHM"と書かれているモードは現在の調波最小PWMモードであり、 "SHE"は選択的調波抑制PWMです。シフトをクリックするとキャリア信号を反転させることができ、これにより出力の形状が変化します。 "Harmonic Setting"をクリックすると、変調された波に調波を追加できます。下のドロップボックスで変調された波を変更できます。
<br>
<br>
「Async」を選択した場合、そのためのいくつかのオプションがあります。 "Dipolar Setting"の下でDipolarバイアスを変更できます。ほとんどの列車はこれを使用しないため、おそらく-1のままで問題ありません。 "Param"の書かれている場所は、キャリア周波数をヘルツ単位で設定する場所です。 "Random"と "Range"の書かれている場所は、キャリア周波数が変動する量、すなわちランダム変調の量です。たとえば、700Hzのキャリア周波数で50Hzの範囲を持つ場合、キャリア周波数は675から725まで範囲内で変動する可能性があります。 "Interval"はキャリア周波数がランダムに変化する頻度です。
<br>
<br>
以下で、設定が通常またはフリーランオフまたはフリーランオンで有効になっているかどうかを選択できます。
<br>
<br>
ここで振幅設定を行います。ほとんどの場合、「Linear」を使用することが望ましいですが、それ以外の場合は他のオプションもあります。プログラムは、2つのポイント間の線を計算するようにして振幅を計算します。 "Start Freq"は振幅設定が始まる出力周波数で、「Start Amp」はその周波数での振幅です。 "End Freq"は振幅設定が終了する出力周波数で、「End Amp」はその周波数での振幅です。 "Max Amp"は許容される最大振幅であり、「Cutoff Amp」は振幅の下限です。 "Dipolar Setting"と "Carrier Frequency Setting"の下にあるドロップダウンメニューを使用して、これらの値が出力周波数に依存するかどうかを変更できます。
<br>
<br>
これで、ブレーキの設定に対しても同じようにこれらの設定が変更されます。
<br>
<br>
これらの設定については、サンプルのVVVFファイルを確認することを強くお勧めします。これらに手を加えると、独自のサウンドを作成する方法がわかりやすくなります。
<br>
<br>

# サポート
- [discord](https://discord.gg/SQr2tXJgVq)に参加してください！VVVFシミュレータに関する質問が頻繁にできます！
- [サンプルファイル](https://github.com/VvvfGeeks/VVVF-Simulator/releases/download/v1.8.0.0/yaml_samples.zip)

# 関連プロジェクト
 - [Raspberry Pi Zero Vvvf](https://github.com/VvvfGeeks/RPi-Zero-VVVF)
 - [Raspberry Pi 3 Vvvf](https://github.com/VvvfGeeks/RPi-3-VVVF)
 - [Youtube](https://www.youtube.com/channel/UCdo7fDodYWO29-Q_0G1S59g)

# 貢献者
 - [Thunderfeng](https://github.com/Leifengfengfeng)
 - [Geek of the Week](https://github.com/geekotw)