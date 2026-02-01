# sijuantianshu
四卷天书修仙文字互动
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="author" content="lulufei999">
  <!-- 手机端自适应核心代码 -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <!-- 优化手机触摸点击体验 -->
  <meta name="msapplication-tap-highlight" content="no">
  <title>四卷天书</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: "Microsoft YaHei", "SimHei", sans-serif;
    }
    body {
      background: #0f172a;
      color: #e2e8f0;
      min-height: 100vh;
      /* 替换为仙侠风背景图 - 高分辨率意境图，适配全屏幕 */
      background-image: url('https://picsum.photos/id/152/1920/1080');
      background-size: cover;
      background-attachment: fixed;
      background-position: center;
      /* 增强背景层次感，避免遮挡文字 */
      background-blend-mode: overlay;
    }
    .scroll-hide {
      overflow: hidden;
    }
    .container {
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
      padding-top: 40px;
      padding-bottom: 80px;
    }
    .title-box {
      text-align: center;
      margin-bottom: 40px;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    }
    .main-title {
      font-size: 36px;
      color: #fbbf24;
      margin-bottom: 10px;
    }
    .sub-title {
      font-size: 18px;
      color: #94a3b8;
    }
    .story-box {
      background: rgba(15, 23, 42, 0.85);
      border-radius: 12px;
      padding: 25px;
      margin-bottom: 30px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(8px);
    }
    .story-title {
      font-size: 24px;
      margin-bottom: 15px;
      color: #fbbf24;
      border-left: 4px solid #fbbf24;
      padding-left: 10px;
    }
    .story-content {
      font-size: 16px;
      line-height: 1.8;
      color: #e2e8f0;
      margin-bottom: 20px;
    }
    .options-box {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .option-btn {
      padding: 15px 20px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
      text-align: left;
      position: relative;
      overflow: hidden;
    }
    .option-btn::after {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
      transition: left 0.5s ease;
    }
    .option-btn:hover::after {
      left: 100%;
    }
    .option-btn:hover {
      transform: translateX(5px);
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
    }
    .choice-tag {
      position: absolute;
      top: 5px;
      right: 10px;
      font-size: 12px;
      padding: 2px 6px;
      border-radius: 4px;
      background: rgba(0, 0, 0, 0.3);
    }
    /* 各天书配色 */
    .primary {
      background: #0f766e;
      color: #ffffff;
    }
    .primary:hover {
      background: #138881;
    }
    .star {
      background: #3b82f6;
      color: #ffffff;
    }
    .star:hover {
      background: #2563eb;
    }
    .devil {
      background: #dc2626;
      color: #ffffff;
    }
    .devil:hover {
      background: #b91c1c;
    }
    .wild {
      background: #c2410c;
      color: #ffffff;
    }
    .wild:hover {
      background: #9a3412;
    }
    .end-box {
      text-align: center;
      padding: 30px;
    }
    .end-title {
      font-size: 30px;
      color: #fbbf24;
      margin-bottom: 20px;
      text-shadow: 0 0 10px rgba(251, 191, 36, 0.5);
    }
    .end-content {
      font-size: 18px;
      line-height: 2;
      margin-bottom: 30px;
      color: #e2e8f0;
    }
    .restart-btn {
      padding: 15px 30px;
      background: #fbbf24;
      color: #0f172a;
      border: none;
      border-radius: 8px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    .restart-btn:hover {
      background: #f59e0b;
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(251, 191, 36, 0.5);
    }
    .trace-box {
      position: fixed;
      top: 20px;
      right: 20px;
      background: rgba(15, 23, 42, 0.9);
      padding: 15px;
      border-radius: 8px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(8px);
      z-index: 9998;
      max-width: 200px;
    }
    .trace-title {
      font-size: 14px;
      color: #94a3b8;
      margin-bottom: 8px;
      text-align: center;
    }
    .trace-list {
      list-style: none;
      font-size: 12px;
      line-height: 1.6;
    }
    .trace-item {
      padding: 3px 0;
      border-bottom: 1px dashed rgba(255, 255, 255, 0.1);
      margin-bottom: 3px;
    }
    .trace-item:last-child {
      border-bottom: none;
      margin-bottom: 0;
    }
    /* 响应式适配 */
    @media (max-width: 768px) {
      .container {
        padding: 15px;
        padding-top: 30px;
        padding-bottom: 90px;
      }
      .main-title {
        font-size: 28px;
      }
      .story-title {
        font-size: 20px;
      }
      .story-content {
        font-size: 15px;
      }
      .option-btn {
        padding: 12px 15px;
        font-size: 15px;
      }
      .end-title {
        font-size: 24px;
      }
      .end-content {
        font-size: 16px;
      }
      .trace-box {
        max-width: 150px;
        padding: 10px;
        top: 10px;
        right: 10px;
      }
      .trace-title {
        font-size: 12px;
      }
      .trace-item {
        font-size: 10px;
      }
    }
  </style>
</head>
<body class="scroll-hide">
  <!-- 背景音乐：西瓜jun《至尊》 -->
  <audio src="https://cdn.jsdelivr.net/gh/yyyymmdddxxx/music-resource@main/zhizun-xiguajun.mp3" loop autoplay preload="auto" controls style="position:fixed;bottom:20px;left:20px;width:120px;opacity:0.3;z-index:9999;">
    您的浏览器不支持音频播放
  </audio>

  <div class="container">
    <div class="title-box" id="start-box">
      <h1 class="main-title">四卷天书</h1>
      <p class="sub-title">一念成仙，一念成魔，大道三千，各取其一</p>
      <div class="options-box" style="margin-top: 40px;">
        <button class="option-btn primary" onclick="goToStory('changsheng')">玄元道宗·长生诀</button>
        <button class="option-btn star" onclick="goToStory('xinghe')">星河仙宗·星河令</button>
        <button class="option-btn devil" onclick="goToStory('tianmo')">天魔古谷·天魔策</button>
        <button class="option-btn wild" onclick="goToStory('dahuang')">大荒圣山·大荒神陨录</button>
      </div>
    </div>

    <div class="story-box" id="story-box" style="display: none;">
      <h2 class="story-title" id="story-title"></h2>
      <div class="story-content" id="story-content"></div>
      <div class="options-box" id="options-box"></div>
    </div>

    <div class="story-box end-box" id="end-box" style="display: none;">
      <h2 class="end-title" id="end-title"></h2>
      <div class="end-content" id="end-content"></div>
      <button class="restart-btn" onclick="restartGame()">重择天书</button>
    </div>
  </div>

  <div class="trace-box" id="trace-box">
    <h3 class="trace-title">选择轨迹</h3>
    <ul class="trace-list" id="trace-list"></ul>
  </div>

  <script>
    // 剧情数据总库
    const storyData = {
      // 长生诀主分支
      changsheng: {
        id: 'changsheng',
        title: '玄元道宗悟长生',
        content: '《长生诀》入手，青芒入体，觉醒先天灵根「乙木灵体」，墓府外恰逢玄元道宗长老云游，见你身蕴长生道韵，收你为亲传弟子，带入玄元山修仙。三载筑基，五载凝液，你深得《长生诀》精髓，可引天地生机疗伤续命，成宗门年轻一辈翘楚。恰逢宗门开启「长生秘境」，秘境核心有「长生莲」，服之可增千年寿元，却也有「心魔莲」混杂其中，取之可速成修为，却会引长生道韵反噬。秘境之中，长生莲与心魔莲并生，你当如何抉择？',
        options: [
          { text: '弃心魔莲，静心采长生莲，循正道修长生', next: 'end1-1', choiceTag: '守正采莲', color: 'primary' },
          { text: '采心魔莲，以力破境，哪怕道韵反噬也要速成', next: 'end1-2', choiceTag: '取魔速成', color: 'primary' },
          { text: '弃莲悟道，不恋寿元不贪速成，归心长生本道', next: 'changsheng-qilian', choiceTag: '弃莲悟道', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 初始分支
      changsheng-qilian: {
        id: 'changsheng-qilian',
        title: '弃莲归心，悟长生本道',
        content: '你望着并生的长生莲与心魔莲，神色淡然，抬手拂去莲瓣上的灵光——既不贪千年寿元，也不恋速成修为，你深知长生之道，从来不在外物，而在本心。转身退出秘境，归返玄元道宗，将秘境所见所悟告知长老，长老赞你「道心纯粹，远超同辈」，赐你《长生诀》下册，引你领悟「心无杂念，方能长生」的真谛。此后你潜心修炼，不参与宗门争斗，不追求境界虚名，每日观天地生机、悟自然之道，筑基十年仍未凝液，却让乙木灵体愈发纯粹，可与天地同息、与草木共生。三百年后，玄元道宗遭遇心魔入侵，长生秘境的心魔莲爆发，无数弟子被心魔侵蚀，长老们束手无策，此时你挺身而出，以纯粹道心引天地生机，暂时压制心魔，却发现心魔根源与上古「心魔幻境」相连，需深入秘境探查根源，途中需接连抉择，方能彻底除魔。',
        options: [
          { text: '孤身深入心魔幻境，不扰同门，独自探查心魔根源', next: 'changsheng-qilian-1', choiceTag: '孤身探境', color: 'primary' },
          { text: '召集宗门精锐弟子，同心协力，共闯心魔幻境', next: 'changsheng-qilian-2', choiceTag: '聚贤除魔', color: 'primary' },
          { text: '先寻上古清心至宝，筑牢道心，再入幻境探根源', next: 'changsheng-qilian-3', choiceTag: '寻宝固心', color: 'primary' },
          { text: '暂封心魔幻境入口，传讯天下仙门，求众仙共解危机', next: 'changsheng-qilian-4', choiceTag: '传讯求援', color: 'primary' },
          { text: '以自身道心为引，温和净化心魔，不诛不灭留一线生机', next: 'changsheng-qilian-5', choiceTag: '道心渡魔', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 分支1
      changsheng-qilian-1: {
        id: 'changsheng-qilian-1',
        title: '孤身探境，道心自守',
        content: '你拒绝同门相助，孤身一人踏入心魔幻境，幻境之中，心魔化作你母亲病重、长老斥责、同辈轻视的虚影，不断扰乱你的道心。你深知幻境皆为虚妄，以《长生诀》下册稳住心神，乙木灵体引天地生机护体，一路披荆斩棘，避开幻境陷阱，终于找到心魔根源——一枚沾染了上古魔气的「道心碎片」。此时碎片引动你的心魔，幻化出「速成修为、长生不死」的诱惑，你当如何？',
        options: [
          { text: '击碎道心碎片，彻底断绝心魔根源，哪怕自身道心受损', next: 'end1-5', choiceTag: '碎片除根', color: 'primary' },
          { text: '炼化道心碎片，以纯粹道心净化魔气，为己所用', next: 'end1-6', choiceTag: '炼化碎片', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 分支2
      changsheng-qilian-2: {
        id: 'changsheng-qilian-2',
        title: '聚贤同心，共破幻境',
        content: '你召集宗门精锐弟子，亲自传授清心之法，以乙木灵体为众人加持生机护盾，一同踏入心魔幻境。幻境之中，弟子们各自陷入心魔考验，有人贪求寿元、有人畏惧死亡，渐渐有人迷失。你一边稳固自身道心，一边引天地生机净化弟子心魔，带领众人突破幻境关卡，抵达心魔根源。此时心魔凝聚成巨影，需有人献祭自身灵元催动宗门秘宝才能击溃，你当如何？',
        options: [
          { text: '自身献祭灵元，催动秘宝击溃心魔，护弟子周全', next: 'end1-7', choiceTag: '献祭护众', color: 'primary' },
          { text: '与弟子们分摊灵元，合力催动秘宝，不求牺牲一人', next: 'end1-8', choiceTag: '合力催宝', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 分支3
      changsheng-qilian-3: {
        id: 'changsheng-qilian-3',
        title: '寻宝固心，稳扎稳打',
        content: '你没有急于入幻境，而是辞别宗门，云游天下寻找上古清心至宝。历经五十年，你在昆仑仙境寻得「清心玉露」，服下后道心愈发纯粹，乙木灵体进化为「先天乙木道体」，可免疫低级心魔侵扰。你携玉露返回玄元道宗，踏入心魔幻境，此时心魔根源的道心碎片已吸收更多魔气，威力大增，但你道心稳固，轻易识破幻境诱惑，直面碎片核心。你当如何处置碎片？',
        options: [
          { text: '以清心玉露净化碎片魔气，将碎片供奉宗门，警醒后世弟子', next: 'end1-9', choiceTag: '净化供奉', color: 'primary' },
          { text: '将清心玉露与碎片相融，炼制成清心法宝，护宗门万年无虞', next: 'end1-10', choiceTag: '炼宝护宗', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 分支4
      changsheng-qilian-4: {
        id: 'changsheng-qilian-4',
        title: '传讯求援，共渡危局',
        content: '你暂封心魔幻境入口，以宗门秘宝传讯天下仙门，告知心魔危机。不久后，玄元道宗汇聚了星河仙宗、万灵谷等各大仙门弟子，众人商议后，决定由你牵头，各仙门合力布下「清心聚灵阵」，压制幻境魔气，再共同深入探查根源。抵达心魔根源后，各仙门因理念不同产生分歧——有的主张彻底击碎碎片，有的主张炼化利用，你作为牵头人，当如何定夺？',
        options: [
          { text: '调和各仙门分歧，以清心聚灵阵净化碎片，达成共识', next: 'end1-11', choiceTag: '调和共识', color: 'primary' },
          { text: '支持彻底击碎碎片，以绝后患，哪怕得罪部分仙门', next: 'end1-12', choiceTag: '力主碎片', color: 'primary' }
        ],
        color: 'primary'
      },
      // 长生诀-放弃双莲 分支5
      changsheng-qilian-5: {
        id: 'changsheng-qilian-5',
        title: '道心渡魔，仁心济世',
        content: '你放弃强攻，以自身道心为引，催动《长生诀》的生机之力，温和包裹心魔幻境，不诛灭心魔，反而引导心魔中的灵智向善。日复一日，你耗费大量灵元，渐渐净化了部分心魔，却发现心魔根源的道心碎片，本是上古一位求道者的残魂，因求道心切沾染魔气才化为心魔。此时残魂向你求救，愿归心向善，你当如何？',
        options: [
          { text: '接纳残魂，以道心引导其净化魔气，共修长生之道', next: 'end1-13', choiceTag: '接纳残魂', color: 'primary' },
          { text: '引导残魂转世投胎，重塑道心，自身继续净化剩余魔气', next: 'end1-14', choiceTag: '引导转世', color: 'primary' }
        ],
        color: 'primary'
      },
      // 星河令主分支
      xinghe: {
        id: 'xinghe',
        title: '星河仙宗掌星力',
        content: '《星河令》入手，星芒灌体，觉醒先天灵根「星辰灵体」，墓府上空星河垂落，星河仙宗宗主亲至，称你为「星河传人」，将你带入星河天宫。你修《星河令》，可引北斗星力炼体，召流星御敌，三载筑基便已能引星芒凝剑，远超同辈。宗门有「星河阵眼」，掌之可调动星河之力，成为下一任宗主，却需以自身灵体为引，永世镇守阵眼；若放弃阵眼，可携《星河令》云游四方，自在修炼，却难登星河道巅峰。阵眼开启，宗主传位在即，你作何选择？',
        options: [
          { text: '承阵眼之责，以灵体镇星河，守宗门万世', next: 'end2-1', choiceTag: '守阵护宗', color: 'star' },
          { text: '弃阵眼之责，携天书云游，求自在登巅峰', next: 'end2-2', choiceTag: '弃阵云游', color: 'star' },
          { text: '弃阵眼亦不云游，不恋权位不贪自在，归心星河本道', next: 'xinghe-qizhen', choiceTag: '弃阵悟道', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 初始分支
      xinghe-qizhen: {
        id: 'xinghe-qizhen',
        title: '弃阵归心，悟星河本道',
        content: '你既不接星河阵眼的镇守之责，也不愿携天书云游四方，直言「星河之力，非阵眼所缚，非天地所限，乃在本心」。宗主见你道心独特，不贪权位不恋自由，赐你《星河令》秘卷「星核篇」，引你领悟「星心同体，星河为心」的真谛。你潜心观星悟道，星辰灵体进化为「星核灵体」，可直接引星河核心之力，却在此时，星河天宫遭遇「星陨之灾」——上古陨星碎片坠入星河，引动星力紊乱，无数星辰陨落，星河阵眼因无人镇守濒临破碎，你需寻陨星根源，接连抉择以救星河。',
        options: [
          { text: '孤身寻陨星根源，以星核灵体硬撼陨星之力，不扰宗门', next: 'xinghe-qizhen-1', choiceTag: '孤身撼星', color: 'star' },
          { text: '召星河仙宗星象师，观星定位陨星根源，合力破局', next: 'xinghe-qizhen-2', choiceTag: '观星合力', color: 'star' },
          { text: '前往星河深处寻「星髓玉」，滋养星核稳固星力，再解灾劫', next: 'xinghe-qizhen-3', choiceTag: '寻玉固核', color: 'star' },
          { text: '传讯星际万族，借异族星力布「星河守护阵」，暂阻星陨', next: 'xinghe-qizhen-4', choiceTag: '联族护星河', color: 'star' },
          { text: '以自身星核为引，牵引紊乱星力，温和归位不毁陨星', next: 'xinghe-qizhen-5', choiceTag: '核引归星', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 分支1
      xinghe-qizhen-1: {
        id: 'xinghe-qizhen-1',
        title: '孤勇撼星，星心无改',
        content: '你孤身踏入星河陨星带，星核灵体引星河核心之力护体，陨星碎片的狂暴星力不断冲击你的灵体，却被你以《星河令》星核篇心法化解。历经三月，你寻得陨星根源——一枚沾染了混沌之力的「陨星核心」，它正不断吞噬星河之力，混沌之力却能引动你星核灵体的潜能，你当如何抉择？',
        options: [
          { text: '击碎陨星核心，彻底断绝混沌之力，哪怕星核灵体受损', next: 'end2-3', choiceTag: '碎核绝沌', color: 'star' },
          { text: '炼化陨星核心，以星核灵体净化混沌之力，为己所用', next: 'end2-4', choiceTag: '炼核化沌', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 分支2
      xinghe-qizhen-2: {
        id: 'xinghe-qizhen-2',
        title: '观星定位，同心破劫',
        content: '你召集宗门星象师，以星核灵体为引，共同推演星象，精准定位陨星根源。你带领星象师、星河战士踏入陨星带，却发现陨星核心引动星力形成「星陨幻阵」，弟子们陷入幻阵，被陨落的恐惧吞噬。你一边以星核之力破阵，一边引导弟子们以星心对抗恐惧，最终抵达陨星核心，却需有人引动自身星力催动「星河碎星炮」才能击溃核心，你当如何？',
        options: [
          { text: '自身引动星力催炮，击溃陨星核心，护弟子周全', next: 'end2-5', choiceTag: '催炮护众', color: 'star' },
          { text: '与弟子分摊星力，合力催动碎星炮，不求一人牺牲', next: 'end2-6', choiceTag: '分力催炮', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 分支3
      xinghe-qizhen-3: {
        id: 'xinghe-qizhen-3',
        title: '寻玉固核，稳解星劫',
        content: '你不急于破劫，前往星河深处的「星髓秘境」，历经百年寻得上古「星髓玉」，服下后星核灵体进化为「先天星河道体」，可免疫混沌星力侵扰，还能自主滋养星河之力。你携星髓玉返回星河天宫，此时陨星核心已吞噬大量星河之力，威力大增，但你星河道体稳固，轻易破去陨星幻阵，直面陨星核心，你当如何处置？',
        options: [
          { text: '以星髓玉净化陨星核心，将核心封印于星河秘境，警醒后世', next: 'end2-7', choiceTag: '净化封印', color: 'star' },
          { text: '将星髓玉与陨星核心相融，炼制成「星河镇核印」，护星河万年', next: 'end2-8', choiceTag: '炼印护星河', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 分支4
      xinghe-qizhen-4: {
        id: 'xinghe-qizhen-4',
        title: '联族借力，共护星河',
        content: '你传讯星际万族（天狼族、灵鹤族、星石族），告知星河星陨之灾，因你平日修星道时曾助各族化解星力危机，各族皆愿相助。你牵头联合万族，布下「星河守护阵」暂阻星陨，再率各族强者踏入陨星带，抵达陨星核心后，各族因处置核心理念分歧——有的主张击碎，有的主张封印，你作为牵头人，当如何定夺？',
        options: [
          { text: '调和各族分歧，以守护阵净化核心，封印于星河共域', next: 'end2-9', choiceTag: '调和封核', color: 'star' },
          { text: '支持击碎核心，以绝后患，哪怕得罪部分主张封印的异族', next: 'end2-10', choiceTag: '力主碎核', color: 'star' }
        ],
        color: 'star'
      },
      // 星河令-放弃阵眼 分支5
      xinghe-qizhen-5: {
        id: 'xinghe-qizhen-5',
        title: '核引星力，温和归位',
        content: '你放弃强攻，以自身星核灵体为引，催动《星河令》星核篇的温和心法，牵引紊乱的星力缓缓归位，不刻意损毁陨星碎片。日复一日，你耗费大量星力，却发现陨星核心并非天生混沌，而是上古星河守护者的「星魂碎片」，因守护星河耗尽星力，被混沌之力侵染才化为灾劫，此时星魂碎片向你求救，愿归心守护星河，你当如何？',
        options: [
          { text: '接纳星魂碎片，以星核灵体净化混沌，共护星河', next: 'end2-11', choiceTag: '纳魂护星河', color: 'star' },
          { text: '引导星魂碎片转世，重塑星心，自身继续归位紊乱星力', next: 'end2-12', choiceTag: '引魂转世', color: 'star' }
        ],
        color: 'star'
      },
      // 天魔策主分支
      tianmo: {
        id: 'tianmo',
        title: '天魔谷中掌魔威',
        content: '《天魔策》入手，暗红魔焰入体，觉醒先天灵根「先天魔体」，墓府外天魔谷谷主寻来，见你魔体纯粹，收你为少谷主，带入天魔谷修魔。你修《天魔策》，可凝魔焰炼魂，化煞气御敌，三年便筑基成魔将，魔威震慑谷中众人。恰逢仙门联军围剿天魔谷，谷主重伤，传你「天魔印」，引之可燃自身魔魂，爆发出超越自身十倍的力量，击退仙门，却会折损千年寿元；若弃天魔印，可率谷中弟子退守魔渊，暂避锋芒，待日后卷土重来。仙门兵临城下，你当抉择？',
        options: [
          { text: '引天魔印，燃魔魂退敌，护天魔谷周全', next: 'end3-1', choiceTag: '燃魂护谷', color: 'devil' },
          { text: '弃天魔印，率弟子退守魔渊，待他日复仇', next: 'end3-2', choiceTag: '退守魔渊', color: 'devil' },
          { text: '弃印亦不退守，不燃魔魂不避锋芒，归心天魔本道', next: 'tianmo-qiyin', choiceTag: '弃印悟道', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 初始分支
      tianmo-qiyin: {
        id: 'tianmo-qiyin',
        title: '弃印归心，悟天魔本道',
        content: '你既不引天魔印燃魔魂，也不率弟子退守魔渊，直言「天魔之道，非蛮力所恃，非避祸所能成，乃在魔心自持」。谷主见你魔心独特，不贪蛮力不恋避祸，将《天魔策》秘卷「魔心篇」传你，引你领悟「魔心无垢，方为真魔」的真谛。你潜心修悟，先天魔体进化为「魔心灵体」，可自由掌控魔焰煞气，却不被其反噬，此时仙门联军并非孤军，竟联合了「除魔盟」，引动上古「除魔剑阵」围困天魔谷，剑阵以正道之力压制魔焰，谷中弟子魔魂受创，你需寻剑阵根源，接连抉择以破阵护谷。',
        options: [
          { text: '孤身闯除魔剑阵，以魔心灵体硬撼剑阵正道之力，独破根源', next: 'tianmo-qiyin-1', choiceTag: '孤身破阵', color: 'devil' },
          { text: '召集谷中魔修强者，凝魔心成阵，合力对抗除魔剑阵', next: 'tianmo-qiyin-2', choiceTag: '凝阵合力', color: 'devil' },
          { text: '前往魔渊深处寻「魔心晶」，滋养魔心稳固魔体，再破剑阵', next: 'tianmo-qiyin-3', choiceTag: '寻晶固心', color: 'devil' },
          { text: '传讯魔道诸宗（血魔谷、幽魔岭），借魔道之力布「天魔守护阵」，暂阻剑阵', next: 'tianmo-qiyin-4', choiceTag: '联宗护谷', color: 'devil' },
          { text: '以自身魔心为引，牵引剑阵正道之力，相融相济不毁剑阵', next: 'tianmo-qiyin-5', choiceTag: '心引融道', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 分支1
      tianmo-qiyin-1: {
        id: 'tianmo-qiyin-1',
        title: '孤勇破阵，魔心无改',
        content: '你孤身闯入除魔剑阵，魔心灵体引纯质魔焰护体，剑阵的正道金光不断冲击你的魔体，却被你以《天魔策》魔心篇心法化解。历经百日，你寻得剑阵根源——一枚蕴满正道之力的「除魔晶核」，它正不断压制魔焰，正道之力却能引动你魔心灵体的潜能，你当如何抉择？',
        options: [
          { text: '击碎除魔晶核，彻底断绝剑阵之力，哪怕魔心灵体受损', next: 'end3-3', choiceTag: '碎核绝阵', color: 'devil' },
          { text: '炼化除魔晶核，以魔心灵体融合正道之力，为己所用', next: 'end3-4', choiceTag: '炼核融道', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 分支2
      tianmo-qiyin-2: {
        id: 'tianmo-qiyin-2',
        title: '凝魔成阵，同心破局',
        content: '你召集谷中魔修强者，以自身魔心灵体为引，凝众魔之心成「天魔同心阵」，硬撼除魔剑阵。却发现除魔晶核引动正道之力形成「正道幻阵」，弟子们陷入幻阵，被「成魔即恶」的执念吞噬，魔心躁动。你一边以魔心之力破阵，一边引导弟子们以真魔心对抗执念，最终抵达除魔晶核，却需有人引动自身魔心催动「天魔碎道炮」才能击溃晶核，你当如何？',
        options: [
          { text: '自身引动魔心催炮，击溃晶核破剑阵，护弟子周全', next: 'end3-5', choiceTag: '催炮护众', color: 'devil' },
          { text: '与弟子分摊魔心之力，合力催动碎道炮，不求一人牺牲', next: 'end3-6', choiceTag: '分力催炮', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 分支3
      tianmo-qiyin-3: {
        id: 'tianmo-qiyin-3',
        title: '寻晶固心，稳破剑阵',
        content: '你不急于破阵，前往魔渊深处的「魔心秘境」，历经五百年寻得上古「魔心晶」，服下后魔心灵体进化为「先天天魔道体」，可免疫正道之力压制，还能自主净化魔焰煞气。你携魔心晶返回天魔谷，此时除魔晶核已吸收大量正道之力，威力大增，但你天魔道体稳固，轻易破去正道幻阵，直面除魔晶核，你当如何处置？',
        options: [
          { text: '以魔心晶融合晶核正道之力，将晶核封印于魔渊，警醒后世', next: 'end3-7', choiceTag: '融力封印', color: 'devil' },
          { text: '将魔心晶与除魔晶核相融，炼制成「天魔镇道印」，护天魔谷万年', next: 'end3-8', choiceTag: '炼印护谷', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 分支4
      tianmo-qiyin-4: {
        id: 'tianmo-qiyin-4',
        title: '联宗借力，共护天魔',
        content: '你传讯魔道诸宗，告知天魔谷被除魔剑阵围困之危，因你平日修魔时曾助诸宗化解正道围剿，诸宗皆愿相助。你牵头联合魔道诸宗，布下「天魔守护阵」暂阻剑阵之力，再率诸宗强者闯入剑阵，抵达除魔晶核后，魔道诸宗因处置晶核理念分歧——有的主张击碎，有的主张炼化，你作为牵头人，当如何定夺？',
        options: [
          { text: '调和诸宗分歧，以守护阵融合晶核之力，封印于魔道共域', next: 'end3-9', choiceTag: '调和封核', color: 'devil' },
          { text: '支持击碎晶核，以绝剑阵后患，哪怕得罪部分主张炼化的魔宗', next: 'end3-10', choiceTag: '力主碎核', color: 'devil' }
        ],
        color: 'devil'
      },
      // 天魔策-放弃天魔印 分支5
      tianmo-qiyin-5: {
        id: 'tianmo-qiyin-5',
        title: '心引融道，魔道共生',
        content: '你放弃强攻，以自身魔心灵体为引，催动《天魔策》魔心篇的温和心法，牵引剑阵的正道之力，与魔焰煞气相融相济，不刻意损毁剑阵。日复一日，你耗费大量魔心之力，却发现除魔晶核并非天生除魔，而是上古一位「道魔双修者」的「道魔魂碎片」，因道魔失衡，被正道强行炼化为除魔晶核，此时魂碎片向你求救，愿归心道魔双修，你当如何？',
        options: [
          { text: '接纳道魔魂碎片，以魔心灵体调和道魔之力，共修天魔道', next: 'end3-11', choiceTag: '纳魂融道', color: 'devil' },
          { text: '引导道魔魂碎片转世，重塑道魔心，自身继续调和剑阵之力', next: 'end3-12', choiceTag: '引魂转世', color: 'devil' }
        ],
        color: 'devil'
      },
      // 大荒神陨录主分支
      dahuang: {
        id: 'dahuang',
        title: '大荒部落炼兽体',
        content: '《大荒神陨录》入手，洪荒古意入体，觉醒先天灵根「大荒兽体」，墓府外大荒部落大萨满寻来，称你为「神陨传人」，将你带入大荒圣山。你修《大荒神陨录》，可引上古神兽之灵炼体，与大荒凶兽沟通，三载筑基便炼出「玄武护体」，肉身强横无匹。大荒圣山有「神兽蛋」，乃上古青龙后裔，温养之可与之结契，共修大道，却需耗费自身十年修为；若取「神兽精血」，可直接炼体，肉身再上一层，却会令青龙后裔身死道消。圣山禁地，神兽蛋与精血皆在，你作何选择？',
        options: [
          { text: '耗修为温养神兽蛋，结契青龙共修大荒道', next: 'end4-1', choiceTag: '温养结契', color: 'wild' },
          { text: '取神兽精血炼体，强肉身哪怕损上古后裔', next: 'end4-2', choiceTag: '取血炼体', color: 'wild' },
          { text: '弃蛋亦弃血，不耗修为不强肉身，归心大荒本道', next: 'dahuang-qiqi', choiceTag: '弃缘悟道', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 初始分支
      dahuang-qiqi: {
        id: 'dahuang-qiqi',
        title: '弃缘归心，悟大荒本道',
        content: '你既不耗修为温养青龙蛋，也不取神兽精血炼体，直言「大荒之道，非神兽所恃，非肉身所能成，乃在本心与万灵共生」。大萨满见你道心独特，不贪神兽助力不恋肉身强横，将《大荒神陨录》秘卷「万灵篇」传你，引你领悟「万灵共生，方为大荒」的真谛。你潜心修悟，大荒兽体进化为「万灵灵体」，可与大荒所有生灵沟通，引万灵之力炼体，却在此时，大荒遭遇「灵枯之灾」——上古「枯灵咒」降临，大荒草木枯萎，凶兽狂躁，神兽灵力衰竭，青龙蛋也因灵力不足濒临破碎，你需寻枯灵咒根源，接连抉择以解灾救大荒。',
        options: [
          { text: '孤身寻枯灵根源，以万灵灵体硬撼枯灵咒力，独解灾劫', next: 'dahuang-qiqi-1', choiceTag: '孤身撼咒', color: 'wild' },
          { text: '召集大荒各族勇士，凝万灵之心成阵，合力对抗枯灵咒', next: 'dahuang-qiqi-2', choiceTag: '凝阵合力', color: 'wild' },
          { text: '前往大荒圣渊寻「万灵晶」，滋养万灵稳固灵体，再解咒劫', next: 'dahuang-qiqi-3', choiceTag: '寻晶固灵', color: 'wild' },
          { text: '传讯大荒万灵（神兽、凶兽、草木族），借万灵之力布「大荒守护阵」，暂阻灵枯', next: 'dahuang-qiqi-4', choiceTag: '联灵护荒', color: 'wild' },
          { text: '以自身万灵心为引，牵引枯灵咒力，转化为生机，不毁咒源', next: 'dahuang-qiqi-5', choiceTag: '心引化枯', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 分支1
      dahuang-qiqi-1: {
        id: 'dahuang-qiqi-1',
        title: '孤勇撼咒，万灵无改',
        content: '你孤身踏入大荒枯灵禁区，万灵灵体引大荒万灵之力护体，枯灵咒的死寂之力不断侵蚀你的灵体，却被你以《大荒神陨录》万灵篇心法化解。历经半年，你寻得枯灵咒根源——一枚蕴满死寂之力的「枯灵晶核」，它正不断吞噬大荒灵力，死寂之力却能引动你万灵灵体的潜能，你当如何抉择？',
        options: [
          { text: '击碎枯灵晶核，彻底断绝死寂之力，哪怕万灵灵体受损', next: 'end4-3', choiceTag: '碎核绝枯', color: 'wild' },
          { text: '炼化枯灵晶核，以万灵灵体转化死寂之力为生机，为己所用', next: 'end4-4', choiceTag: '炼核化枯', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 分支2
      dahuang-qiqi-2: {
        id: 'dahuang-qiqi-2',
        title: '凝灵成阵，同心解劫',
        content: '你召集大荒各族勇士，以自身万灵灵体为引，凝大荒万灵之心成「大荒同心阵」，硬撼枯灵咒。却发现枯灵晶核引动死寂之力形成「枯灵幻阵」，族人陷入幻阵，被大荒枯萎的绝望吞噬，万灵心躁动。你一边以万灵之力破阵，一边引导族人以共生心对抗绝望，最终抵达枯灵晶核，却需有人引动自身万灵之力催动「大荒生息炮」才能击溃晶核，你当如何？',
        options: [
          { text: '自身引动万灵力催炮，击溃晶核解咒劫，护族人周全', next: 'end4-5', choiceTag: '催炮护众', color: 'wild' },
          { text: '与族人分摊万灵力，合力催动生息炮，不求一人牺牲', next: 'end4-6', choiceTag: '分力催炮', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 分支3
      dahuang-qiqi-3: {
        id: 'dahuang-qiqi-3',
        title: '寻晶固灵，稳解咒劫',
        content: '你不急于解劫，前往大荒圣渊的「万灵秘境」，历经千年寻得上古「万灵晶」，服下后万灵灵体进化为「先天大荒道体」，可免疫死寂之力侵蚀，还能自主滋养大荒灵力。你携万灵晶返回大荒圣山，此时枯灵晶核已吸收大量大荒灵力，威力大增，但你大荒道体稳固，轻易破去枯灵幻阵，直面枯灵晶核，你当如何处置？',
        options: [
          { text: '以万灵晶转化晶核死寂之力，将晶核封印于圣渊，警醒后世', next: 'end4-7', choiceTag: '化力封印', color: 'wild' },
          { text: '将万灵晶与枯灵晶核相融，炼制成「大荒镇枯印」，护大荒万年', next: 'end4-8', choiceTag: '炼印护荒', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 分支4
      dahuang-qiqi-4: {
        id: 'dahuang-qiqi-4',
        title: '联灵借力，共护大荒',
        content: '你传讯大荒万灵，告知大荒灵枯之灾，因你平日修大荒道时曾助万灵化解危机，万灵皆愿相助。你牵头联合大荒万灵，布下「大荒守护阵」暂阻灵枯之势，再率万灵强者踏入枯灵禁区，抵达枯灵晶核后，万灵因处置晶核理念分歧——有的主张击碎，有的主张转化，你作为牵头人，当如何定夺？',
        options: [
          { text: '调和万灵分歧，以守护阵转化晶核之力，封印于大荒共域', next: 'end4-9', choiceTag: '调和封核', color: 'wild' },
          { text: '支持击碎晶核，以绝死寂后患，哪怕得罪部分主张转化的生灵', next: 'end4-10', choiceTag: '力主碎核', color: 'wild' }
        ],
        color: 'wild'
      },
      // 大荒神陨录-放弃双机缘 分支5
      dahuang-qiqi-5: {
        id: 'dahuang-qiqi-5',
        title: '心引化枯，万灵共生',
        content: '你放弃强攻，以自身万灵灵体为引，催动《大荒神陨录》万灵篇的温和心法，牵引枯灵咒的死寂之力，将其缓缓转化为大荒生机，不刻意损毁晶核。日复一日，你耗费大量万灵之力，却发现枯灵晶核并非天生死寂，而是上古「大荒守护者」的「万灵魂碎片」，因守护大荒耗尽灵力，被死寂之力侵染才化为灾劫，此时魂碎片向你求救，愿归心守护大荒，你当如何？',
        options: [
          { text: '接纳万灵魂碎片，以万灵灵体净化死寂之力，共护大荒', next: 'end4-11', choiceTag: '纳魂护荒', color: 'wild' },
          { text: '引导万灵魂碎片转世，重塑万灵心，自身继续转化死寂之力', next: 'end4-12', choiceTag: '引魂转世', color: 'wild' }
        ],
        color: 'wild'
      },
      // 结局库-长生诀
      'end1-1': { id: 'end1-1', title: '长生仙尊', content: '你弃心魔莲而采长生莲，药力入体，千年寿元加身，乙木灵体愈发纯粹，道心无垢，修为稳步提升。百年结丹，五百年化婴，千年炼虚，最终悟透长生大道，证道「长生仙尊」，坐镇玄元道宗，引天地生机滋养宗门，护佑一方仙道昌盛，寿元与天地同齐，成为修仙界不朽的传说。【结局：长生仙尊，道泽万世】', isEnd: true, color: 'primary' },
      'end1-2': { id: 'end1-2', title: '短命魔仙', content: '你采下心魔莲，药力入体，修为一日千里，半年便凝液，一年便结丹，却也引长生道韵反噬，乙木灵体受损，寿元折损九成。你虽成一方魔仙，战力强横，却活不过三十载，最终在寿元耗尽之际，坐化于玄元山脚下，临终前悔悟，却已无力回天，只留一句「长生非速，守心方久」。【结局：短命魔仙，悔不当初】', isEnd: true, color: 'primary' },
      'end1-3': { id: 'end1-3', title: '长生真人', content: '你以纯粹道心压制心魔，不耗自身灵元，转而引导天地生机，滋养被心魔侵蚀的弟子，同时寻得「清心莲」，搭配《长生诀》下册，成功研制出除魔丹，既净化了秘境心魔，又保全了自身修为。此后你继续潜心悟道，不追寿元、不恋权位，百年结丹，五百年化婴，最终悟透长生本道，证道「长生真人」，寿元绵长却不执着，常年云游四方，以道心渡化世人，成为修仙界道心的标杆。【结局：长生真人，道心永存】', isEnd: true, color: 'primary' },
      'end1-4': { id: 'end1-4', title: '道心圣祖', content: '你毅然耗尽自身乙木灵元，引天地生机化作清心之光，笼罩整个玄元道宗，净化了所有心魔，包括秘境中的心魔莲本源。灵元耗尽之际，你的道心却突破桎梏，肉身虽陨，神魂却与天地生机相融，化作「道心圣像」，坐镇玄元山秘境，庇佑宗门万年无虞。后世修士皆以你为榜样，铭记「长生在心，不在外物」的至理，你也被尊为「道心圣祖」，名垂仙史，万古流芳。【结局：道心圣祖，神魂不朽】', isEnd: true, color: 'primary' },
      'end1-5': { id: 'end1-5', title: '孤绝道君', content: '你击碎道心碎片，彻底断绝心魔根源，自身道心虽受重创，却始终未曾动摇。返回玄元道宗后，你闭门修炼百年，以天地生机修复道心，乙木灵体愈发纯粹，最终悟透「孤绝道心」的真谛，证道「孤绝道君」。你不恋宗门权位，不结仙缘，常年隐居玄元山深处，偶尔下山渡化道心不坚的修士，虽孤寂一生，却道心永存，寿元绵长。【结局：孤绝道君，道心无垢】', isEnd: true, color: 'primary' },
      'end1-6': { id: 'end1-6', title: '融魔道尊', content: '你以纯粹道心为引，炼化道心碎片中的魔气，将碎片融入自身道心，既没有被魔气侵蚀，反而借魔气之力完善《长生诀》，创造出「心魔长生道」。你突破桎梏，证道「融魔道尊」，可自由掌控魔气与生机，既不做正道楷模，也不做魔道枭雄，独树一帜，常年云游天下，探寻长生终极奥秘，成为修仙界最神秘的存在。【结局：融魔道尊，独树一帜】', isEnd: true, color: 'primary' },
      'end1-7': { id: 'end1-7', title: '护宗圣君', content: '你毅然献祭自身灵元，催动宗门秘宝，击溃心魔巨影，彻底化解玄元道宗危机，而你自身则灵元耗尽，肉身濒临消散。万幸你道心纯粹，乙木灵体与天地生机深度绑定，神魂未灭，被长老们以宗门至宝护住，历经千年重塑肉身，最终证道「护宗圣君」，坐镇玄元道宗，庇佑宗门弟子，成为宗门万年以来最受敬仰的圣祖之一。【结局：护宗圣君，宗门永庇】', isEnd: true, color: 'primary' },
      'end1-8': { id: 'end1-8', title: '同心道祖', content: '你与弟子们分摊灵元，合力催动秘宝，击溃心魔巨影，众人虽灵元受损，却无一人牺牲。经此一役，你与弟子们道心皆有突破，你更是悟透「同心悟道」的真谛，带领玄元道宗走向鼎盛，最终证道「同心道祖」，创立「同心道派」，主张仙门同心、道心共生，被天下仙门奉为楷模，名垂万古。【结局：同心道祖，仙门共尊】', isEnd: true, color: 'primary' },
      'end1-9': { id: 'end1-9', title: '清心道君', content: '你以清心玉露净化道心碎片，将碎片供奉于宗门秘境，警醒后世弟子「道心不可贪，外物不可恋」。此后你潜心悟道，先天乙木道体引天地生机，百年结丹、五百年化婴、千年证道，成为「清心道君」。你一生谨慎自持，道心无一丝杂质，常年驻守宗门，传授弟子清心之道，让玄元道宗成为修仙界道心最纯粹的宗门。【结局：清心道君，道统相传】', isEnd: true, color: 'primary' },
      'end1-10': { id: 'end1-10', title: '镇宗道君', content: '你将清心玉露与道心碎片相融，炼制成「清心道印」，此印可净化心魔、稳固道心，成为玄元道宗的镇宗之宝。你凭借先天乙木道体与清心道印，修为一日千里，最终证道「镇宗道君」，坐镇玄元道宗秘境，以清心道印护宗门万年无虞，弟子们皆以你为榜样，潜心修炼，不贪速成、不恋寿元，宗门愈发鼎盛。【结局：镇宗道君，宝护宗门】', isEnd: true, color: 'primary' },
      'end1-11': { id: 'end1-11', title: '调和道祖', content: '你调和各仙门分歧，以清心聚灵阵净化道心碎片，既没有击碎浪费，也没有炼化私用，而是将碎片供奉于天下仙门共有的「仙宗圣殿」，警醒天下修士。经此一役，你声名远播，被各仙门推举为「调和道祖」，主张仙门同心、道心共生，化解仙门之间的纷争，推动修仙界走向和平，最终与天地生机相融，成为修仙界的精神象征。【结局：调和道祖，仙界共生】', isEnd: true, color: 'primary' },
      'end1-12': { id: 'end1-12', title: '果决道君', content: '你力排众议，主张彻底击碎道心碎片，以绝后患，虽得罪部分主张炼化碎片的仙门，却彻底化解了心魔危机。此后你返回玄元道宗，潜心悟道，凭借果决道心与先天乙木灵体，最终证道「果决道君」。你一生行事果决，不优柔寡断，道心纯粹，常年云游天下，斩除心魔隐患，成为修仙界最令人信服的道君之一。【结局：果决道君，斩魔无优】', isEnd: true, color: 'primary' },
      'end1-13': { id: 'end1-13', title: '仁心道祖', content: '你接纳上古求道者残魂，以自身道心引导其净化魔气，与残魂共修长生之道，残魂也将自身上古求道经验传授于你。你借此悟透「仁心渡世」的真谛，先天乙木灵体进化为「万灵道体」，可引万灵之力渡化心魔，最终证道「仁心道祖」。你走遍天下，渡化所有被困心魔，引导世人向善，成为修仙界仁心的象征，寿元无尽，万古流芳。【结局：仁心道祖，渡化众生】', isEnd: true, color: 'primary' },
      'end1-14': { id: 'end1-14', title: '渡世道君', content: '你引导上古求道者残魂转世投胎，重塑道心，自身则继续耗费灵元，温和净化心魔幻境剩余魔气，让秘境恢复生机。此后你潜心悟道，悟透「渡世不渡己」的真谛，常年云游四方，渡化道心不坚、沾染魔气的修士，最终证道「渡世道君」。你不追求自身长生极致，却以渡世为己任，被天下修士敬仰，神魂与天地共生，永世不灭。【结局：渡世道君，永世渡人】', isEnd: true, color: 'primary' },
      // 结局库-星河令
      'end2-1': { id: 'end2-1', title: '星河帝君', content: '你承下星河阵眼之责，以星辰灵体为引，永世镇守星河天宫，星河之力随你心意而动，可召亿万星辰降世，威力无穷。你成为星河仙宗史上最年轻的宗主，带领宗门走向鼎盛，威压整个星际，最终证道「星河帝君」，与星河同生共死，成为星际中不朽的星辰之主，万族敬仰，名垂星际万古。【结局：星河帝君，星耀万古】', isEnd: true, color: 'star' },
      'end2-2': { id: 'end2-2', title: '逍遥星仙', content: '你弃星河阵眼之责，携《星河令》云游星际四方，不被宗门束缚，不恋权位虚名，在星际中寻幽探胜，遇强则强，遇弱则扶。你修得一身绝世星力，可自由穿梭星际，逍遥自在，最终证道「逍遥星仙」，无拘无束，与星辰为伴，笑看星际变迁，成为星际中最洒脱的存在。【结局：逍遥星仙，无拘无束】', isEnd: true, color: 'star' },
      'end2-3': { id: 'end2-3', title: '孤绝星君', content: '你击碎陨星核心，彻底断绝混沌之力，自身星核灵体虽受重创，却始终星心坚定。返回星河天宫后，你闭门修炼千年，以星河核心之力修复灵体，星核灵体愈发纯粹，最终悟透「孤绝星道」，证道「孤绝星君」。你不恋宗门权位，不结星际仙缘，常年隐居星河核心，偶尔引星力渡化星际迷途者，虽孤寂一生，却星心永存，与星河同寿。【结局：孤绝星君，星心无垢】', isEnd: true, color: 'star' },
      'end2-4': { id: 'end2-4', title: '混沌星尊', content: '你以星核灵体为引，炼化陨星核心中的混沌之力，将混沌与星河之力相融，创造出「混沌星河道」，突破星河道极致桎梏。你证道「混沌星尊」，可自由掌控星河与混沌之力，既不做星河楷模，也不做星际霸主，独游星际之间，探寻星河终极奥秘，成为星际中最神秘的存在。【结局：混沌星尊，独步星际】', isEnd: true, color: 'star' },
      'end2-5': { id: 'end2-5', title: '护星圣君', content: '你毅然引动自身星力，催动星河碎星炮击溃陨星核心，彻底化解星陨之灾，而你自身星力耗尽，灵体濒临消散。万幸你星心纯粹，星河道体与星河核心深度绑定，星魂未灭，被宗主以星河至宝护住，历经万年重塑灵体，最终证道「护星圣君」，坐镇星河天宫，庇佑星际万族，成为星河万年以来最受敬仰的圣祖。【结局：护星圣君，星河永庇】', isEnd: true, color: 'star' },
      'end2-6': { id: 'end2-6', title: '同心星祖', content: '你与弟子们分摊星力，合力催动星河碎星炮，击溃陨星核心，众人虽星力受损，却无一人牺牲。经此一役，你与弟子们星心皆有突破，你更是悟透「同心星道」的真谛，带领星河仙宗走向鼎盛，联合星际万族创立「星河同盟」，最终证道「同心星祖」，被星际万族奉为共主，名垂星际万古。【结局：同心星祖，星际共尊】', isEnd: true, color: 'star' },
      'end2-7': { id: 'end2-7', title: '清星河君', content: '你以星髓玉净化陨星核心的混沌之力，将核心封印于星河秘境，立下祖训「星力不可贪，混沌不可近」，警醒后世弟子。此后你潜心悟道，先天星河道体引星河核心之力，千年凝星核，万年证道，成为「清星河君」。你一生谨慎自持，星心无一丝杂质，常年驻守星河秘境，传授弟子清星之道，让星河仙宗成为星际中星心最纯粹的宗门。【结局：清星河君，星道相传】', isEnd: true, color: 'star' },
      'end2-8': { id: 'end2-8', title: '镇星河君', content: '你将星髓玉与陨星核心相融，炼制成「星河镇核印」，此印可净化混沌星力、稳固星河本源，成为星河天宫的镇宗至宝。你凭借先天星河道体与镇核印，星力一日千里，最终证道「镇星河君」，坐镇星河核心，以镇核印护星河万年无虞，星际万族皆来朝拜，星河仙宗成为星际第一宗门。【结局：镇星河君，宝护星河】', isEnd: true, color: 'star' },
      'end2-9': { id: 'end2-9', title: '调和星祖', content: '你调和星际万族分歧，以星河守护阵净化陨星核心，将核心封印于星际万族共有的「星河圣殿」，警醒全星际。经此一役，你声名远播，被万族推举为「调和星祖」，主张星际同心、星心共生，化解星际各族纷争，推动星际走向和平，最终与星河核心相融，成为星际的精神象征。【结局：调和星祖，星际共生】', isEnd: true, color: 'star' },
      'end2-10': { id: 'end2-10', title: '果决星君', content: '你力排众议，主张彻底击碎陨星核心，以绝混沌后患，虽得罪部分主张封印的异族，却彻底化解了星陨之灾。此后你返回星河天宫，潜心悟道，凭借果决星心与先天星河道体，最终证道「果决星君」。你一生行事果决，不优柔寡断，星心纯粹，常年游弋星际，斩除混沌星力隐患，成为星际最令人信服的星君。【结局：果决星君，斩沌无忧】', isEnd: true, color: 'star' },
      'end2-11': { id: 'end2-11', title: '仁星河祖', content: '你接纳上古星河守护者的星魂碎片，以星核灵体净化其混沌之力，与星魂共护星河，星魂也将上古星河守护之法传授于你。你借此悟透「仁心护星」的真谛，先天星河道体进化为「万星道体」，可引万星之力净化混沌，最终证道「仁星河祖」。你走遍星际，渡化所有混沌星力，守护星际万族，成为星际仁心的象征，与星河同寿，万古流芳。【结局：仁星河祖，护佑星际】', isEnd: true, color: 'star' },
      'end2-12': { id: 'end2-12', title: '渡星际君', content: '你引导上古星河守护者的星魂碎片转世投胎，重塑星心，自身则继续耗费星力，温和归位紊乱的星河之力，让星河恢复生机。此后你潜心悟道，悟透「渡星不渡己」的真谛，常年游弋星际，渡化星际迷途者、净化零散混沌星力，最终证道「渡星际君」。你不追求自身星力极致，却以护星渡世为己任，被星际万族敬仰，星魂与星河共生，永世不灭。【结局：渡星际君，永世护星】', isEnd: true, color: 'star' },
      // 结局库-天魔策
      'end3-1': { id: 'end3-1', title: '天魔圣祖', content: '你引动天魔印，燃自身魔魂爆发出十倍力量，魔焰滔天，一击便击溃仙门联军，护得天魔谷周全。虽折损千年寿元，却因护谷之功被谷中弟子奉若神明，谷主传位与你，你带领天魔谷休养生息，威压魔道诸宗，最终证道「天魔圣祖」，成为魔道至高无上的存在，魔名震彻三界，无人敢惹。【结局：天魔圣祖，魔威盖世】', isEnd: true, color: 'devil' },
      'end3-2': { id: 'end3-2', title: '复仇魔尊', content: '你弃天魔印，率谷中弟子退守魔渊，忍辱负重，潜心修炼《天魔策》，融合魔渊煞气，魔功大进。百年后，你率魔渊大军卷土重来，魔焰所到之处仙门皆灭，血洗当年围剿天魔谷的仙门联军，大仇得报，最终证道「复仇魔尊」，独霸一方，成为三界中令人闻风丧胆的存在。【结局：复仇魔尊，血洗仙门】', isEnd: true, color: 'devil' },
      'end3-3': { id: 'end3-3', title: '孤绝魔君', content: '你击碎除魔晶核，彻底断绝除魔剑阵之力，自身魔心灵体虽受重创，却始终魔心坚定。返回天魔谷后，你闭门修炼五千年，以魔渊煞气修复灵体，魔心灵体愈发纯粹，最终悟透「孤绝魔道」，证道「孤绝魔君」。你不恋谷中权位，不结魔道之缘，常年隐居魔渊深处，偶尔引纯质魔焰渡化魔道迷途者，虽孤寂一生，却魔心永存，与魔渊同寿。【结局：孤绝魔君，魔心无垢】', isEnd: true, color: 'devil' },
      'end3-4': { id: 'end3-4', title: '道魔魔尊', content: '你以魔心灵体为引，炼化除魔晶核中的正道之力，将道与魔之力相融，创造出「道魔双休道」，突破天魔道极致桎梏。你证道「道魔魔尊」，可自由掌控魔焰与正道之力，既不做魔道楷模，也不做正道仇敌，独走三界之间，探寻道魔终极奥秘，成为三界中最神秘的存在。【结局：道魔魔尊，独步三界】', isEnd: true, color: 'devil' },
      'end3-5': { id: 'end3-5', title: '护魔圣君', content: '你毅然引动自身魔心，催动天魔碎道炮击溃除魔晶核，彻底化解剑阵之危，而你自身魔心之力耗尽，魔体濒临消散。万幸你魔心纯粹，天魔道体与魔渊煞气深度绑定，魔魂未灭，被谷主以天魔至宝护住，历经十万年重塑魔体，最终证道「护魔圣君」，坐镇天魔谷，庇佑魔道诸宗，成为魔道万年以来最受敬仰的圣祖。【结局：护魔圣君，魔道永庇】', isEnd: true, color: 'devil' },
      'end3-6': { id: 'end3-6', title: '同心魔祖', content: '你与弟子们分摊魔心之力，合力催动天魔碎道炮，击溃除魔晶核，众人虽魔心受损，却无一人牺牲。经此一役，你与弟子们魔心皆有突破，你更是悟透「同心魔道」的真谛，带领天魔谷走向鼎盛，联合魔道诸宗创立「魔道同盟」，最终证道「同心魔祖」，被魔道诸宗奉为共主，名垂魔道万古。【结局：同心魔祖，魔道共尊】', isEnd: true, color: 'devil' },
      'end3-7': { id: 'end3-7', title: '清心魔君', content: '你以魔心晶融合除魔晶核的正道之力，将晶核封印于魔渊秘境，立下祖训「魔力不可贪，正道不可忌」，警醒后世弟子。此后你潜心悟道，先天天魔道体引魔渊纯质煞气，千年凝魔心，万年证道，成为「清心魔君」。你一生谨慎自持，魔心无一丝杂质，常年驻守魔渊秘境，传授弟子清心魔道，让天魔谷成为魔道中魔心最纯粹的宗门。【结局：清心魔君，魔道相传】', isEnd: true, color: 'devil' },
      'end3-8': { id: 'end3-8', title: '镇天魔君', content: '你将魔心晶与除魔晶核相融，炼制成「天魔镇道印」，此印可融合道魔之力、压制除魔剑阵，成为天魔谷的镇宗至宝。你凭借先天天魔道体与镇道印，魔力一日千里，最终证道「镇天魔君」，坐镇魔渊深处，以镇道印护天魔谷万年无虞，魔道诸宗皆来朝拜，天魔谷成为魔道第一宗门。【结局：镇天魔君，宝护天魔】', isEnd: true, color: 'devil' },
      'end3-9': { id: 'end3-9', title: '调和魔祖', content: '你调和魔道诸宗分歧，以天魔守护阵融合除魔晶核之力，将晶核封印于魔道诸宗共有的「天魔圣殿」，警醒全魔道。经此一役，你声名远播，被诸宗推举为「调和魔祖」，主张魔道同心、魔心共生，化解魔道诸宗纷争，推动魔道走向有序，最终与魔渊煞气相融，成为魔道的精神象征。【结局：调和魔祖，魔道共生】', isEnd: true, color: 'devil' },
      'end3-10': { id: 'end3-10', title: '果决魔君', content: '你力排众议，主张彻底击碎除魔晶核，以绝剑阵后患，虽得罪部分主张炼化的魔宗，却彻底化解了天魔谷之危。此后你返回天魔谷，潜心悟道，凭借果决魔心与先天天魔道体，最终证道「果决魔君」。你一生行事果决，不优柔寡断，魔心纯粹，常年游弋三界，斩除除魔剑阵隐患，成为魔道最令人信服的魔君。【结局：果决魔君，斩阵无忧】', isEnd: true, color: 'devil' },
      'end3-11': { id: 'end3-11', title: '仁心魔祖', content: '你接纳上古道魔双修者的道魔魂碎片，以魔心灵体调和其道魔失衡之力，与魂碎片共修天魔道，魂碎片也将上古道魔双修之法传授于你。你借此悟透「仁心护魔」的真谛，先天天魔道体进化为「万魔道体」，可引万魔之力融合正道，最终证道「仁心魔祖」。你走遍三界，渡化魔道迷途者，调和道魔纷争，成为魔道仁心的象征，与魔渊同寿，万古流芳。【结局：仁心魔祖，护佑魔道】', isEnd: true, color: 'devil' },
      'end3-12': { id: 'end3-12', title: '渡魔魔君', content: '你引导上古道魔双修者的道魔魂碎片转世投胎，重塑道魔心，自身则继续耗费魔心之力，温和调和除魔剑阵的正道之力，让天魔谷恢复生机。此后你潜心悟道，悟透「渡魔不渡己」的真谛，常年游弋三界，渡化魔道迷途者、调和零散道魔纷争，最终证道「渡魔魔君」。你不追求自身魔力极致，却以护魔渡世为己任，被魔道诸宗敬仰，魔魂与魔渊共生，永世不灭。【结局：渡魔魔君，永世护魔】', isEnd: true, color: 'devil' },
      // 结局库-大荒神陨录
      'end4-1': { id: 'end4-1', title: '大荒圣主', content: '你耗费十年修为温养青龙蛋，成功与上古青龙后裔结契，青龙伴身，可引四海之水、唤雷霆之力，肉身与神兽之力相融，大荒兽体进化为「青龙兽体」。你成为大荒部落史上最强的萨满，带领大荒万灵繁衍生息，抵御外敌，最终证道「大荒圣主」，与青龙共护大荒，成为大荒万灵心中不朽的守护神，名垂大荒万古。【结局：大荒圣主，万灵共尊】', isEnd: true, color: 'wild' },
      'end4-2': { id: 'end4-2', title: '蛮荒战神', content: '你取神兽精血炼体，精血入体，肉身强横到极致，大荒兽体进化为「蛮荒战体」，一拳可碎山裂地，无人能挡。却因灭杀青龙后裔，触怒大荒万灵，被大萨满驱逐，你独走大荒，以战证道，遇神杀神，遇佛杀佛，最终证道「蛮荒战神」，独霸大荒一方，却也终生被万灵所弃，孤寂一生。【结局：蛮荒战神，万灵皆弃】', isEnd: true, color: 'wild' },
      'end4-3': { id: 'end4-3', title: '孤绝荒君', content: '你击碎枯灵晶核，彻底断绝死寂之力，自身万灵灵体虽受重创，却始终万灵心坚定。返回大荒圣山后，你闭门修炼万年，以大荒万灵之力修复灵体，万灵灵体愈发纯粹，最终悟透「孤绝荒道」，证道「孤绝荒君」。你不恋部落权位，不结万灵之缘，常年隐居大荒圣渊，偶尔引万灵之力渡化大荒迷途生灵，虽孤寂一生，却万灵心永存，与大荒同寿。【结局：孤绝荒君，万灵无垢】', isEnd: true, color: 'wild' },
      'end4-4': { id: 'end4-4', title: '枯生荒尊', content: '你以万灵灵体为引，炼化枯灵晶核中的死寂之力，将死寂与生机之力相融，创造出「枯生大荒道」，突破大荒道极致桎梏。你证道「枯生荒尊」，可自由掌控死寂与生机之力，既不做大荒楷模，也不做万灵霸主，独走大荒之间，探寻大荒终极奥秘，成为大荒中最神秘的存在。【结局：枯生荒尊，独步大荒】', isEnd: true, color: 'wild' },
      'end4-5': { id: 'end4-5', title: '护荒圣君', content: '你毅然引动自身万灵之力，催动大荒生息炮击溃枯灵晶核，彻底化解灵枯之灾，而你自身万灵之力耗尽，灵体濒临消散。万幸你万灵心纯粹，大荒道体与大荒万灵深度绑定，神魂未灭，被大萨满以大荒至宝护住，历经十万年重塑灵体，最终证道「护荒圣君」，坐镇大荒圣山，庇佑大荒万灵，成为大荒万年以来最受敬仰的圣祖。【结局：护荒圣君，大荒永庇】', isEnd: true, color: 'wild' },
      'end4-6': { id: 'end4-6', title: '同心荒祖', content: '你与族人分摊万灵之力，合力催动大荒生息炮，击溃枯灵晶核，众人虽万灵之力受损，却无一人牺牲。经此一役，你与族人万灵心皆有突破，你更是悟透「同心荒道」的真谛，带领大荒部落走向鼎盛，联合大荒万灵创立「大荒同盟」，最终证道「同心荒祖」，被大荒万灵奉为共主，名垂大荒万古。【结局：同心荒祖，大荒共尊】', isEnd: true, color: 'wild' },
      'end4-7': { id: 'end4-7', title: '清荒君', content: '你以万灵晶转化枯灵晶核的死寂之力，将晶核封印于大荒圣渊，立下祖训「灵力不可贪，死寂不可近」，警醒后世族人。此后你潜心悟道，先天大荒道体引大荒万灵之力，千年凝万灵心，万年证道，成为「清荒君」。你一生谨慎自持，万灵心无一丝杂质，常年驻守大荒圣渊，传授弟子清荒之道，让大荒部落成为大荒中万灵心最纯粹的族群。【结局：清荒君，荒道相传】', isEnd: true, color: 'wild' },
      'end4-8': { id: 'end4-8', title: '镇荒君', content: '你将万灵晶与枯灵晶核相融，炼制成「大荒镇枯印」，此印可转化死寂之力、滋养大荒万灵，成为大荒圣山的镇族至宝。你凭借先天大荒道体与镇枯印，万灵之力一日千里，最终证道「镇荒君」，坐镇大荒圣渊，以镇枯印护大荒万年无虞，大荒万灵皆来朝拜，大荒部落成为大荒第一族群。【结局：镇荒君，宝护大荒】', isEnd: true, color: 'wild' },
      'end4-9': { id: 'end4-9', title: '调和荒祖', content: '你调和大荒万灵分歧，以大荒守护阵转化枯灵晶核之力，将晶核封印于大荒万灵共有的「大荒圣殿」，警醒全大荒。经此一役，你声名远播，被万灵推举为「调和荒祖」，主张大荒同心、万灵共生，化解大荒各族纷争，推动大荒走向和平，最终与大荒万灵相融，成为大荒的精神象征。【结局：调和荒祖，大荒共生】', isEnd: true, color: 'wild' },
      'end4-10': { id: 'end4-10', title: '果决荒君', content: '你力排众议，主张彻底击碎枯灵晶核，以绝死寂后患，虽得罪部分主张转化的生灵，却彻底化解了大荒灵枯之灾。此后你返回大荒圣山，潜心悟道，凭借果决万灵心与先天大荒道体，最终证道「果决荒君」。你一生行事果决，不优柔寡断，万灵心纯粹，常年游弋大荒，斩除死寂之力隐患，成为大荒最令人信服的荒君。【结局：果决荒君，斩枯无忧】', isEnd: true, color: 'wild' },
      'end4-11': { id: 'end4-11', title: '仁心荒祖', content: '你接纳上古大荒守护者的万灵魂碎片，以万灵灵体净化其死寂之力，与魂碎片共护大荒，魂碎片也将上古大荒守护之法传授于你。你借此悟透「仁心护荒」的真谛，先天大荒道体进化为「大荒万灵道体」，可引大荒万灵之力转化死寂，最终证道「仁心荒祖」。你走遍大荒，渡化所有死寂之力，守护大荒万灵，成为大荒仁心的象征，与大荒同寿，万古流芳。【结局：仁心荒祖，护佑大荒】', isEnd: true, color: 'wild' },
      'end4-12': { id: 'end4-12', title: '渡荒君', content: '你引导上古大荒守护者的万灵魂碎片转世投胎，重塑万灵心，自身则继续耗费万灵之力，温和转化大荒的死寂之力，让大荒恢复生机。此后你潜心悟道，悟透「渡荒不渡己」的真谛，常年游弋大荒，渡化大荒迷途生灵、转化零散死寂之力，最终证道「渡荒君」。你不追求自身万灵之力极致，却以护荒渡世为己任，被大荒万灵敬仰，神魂与大荒共生，永世不灭。【结局：渡荒君，永世护荒】', isEnd: true, color: 'wild' }
    };

    // 选择轨迹数组
    let choiceTrace = [];

    // 进入剧情
    function goToStory(storyId) {
      const story = storyData[storyId];
      if (!story) return;
      // 隐藏开始页，显示剧情页
      document.getElementById('start-box').style.display = 'none';
      const storyBox = document.getElementById('story-box');
      storyBox.style.display = 'block';
      document.getElementById('end-box').style.display = 'none';
      // 设置剧情标题和内容
      document.getElementById('story-title').innerText = story.title;
      document.getElementById('story-content').innerText = story.content;
      // 生成选项按钮
      const optionsBox = document.getElementById('options-box');
      optionsBox.innerHTML = '';
      story.options.forEach(option => {
        const btn = document.createElement('button');
        btn.className = `option-btn ${option.color || story.color}`;
        btn.innerText = option.text;
        // 添加选择标签
        if (option.choiceTag) {
          const tag = document.createElement('span');
          tag.className = 'choice-tag';
          tag.innerText = option.choiceTag;
          btn.appendChild(tag);
        }
        // 绑定点击事件
        btn.onclick = () => {
          // 记录选择轨迹
          if (option.choiceTag) {
            choiceTrace.push(option.choiceTag);
            updateTrace();
          }
          // 跳转下一个剧情/结局
          const nextId = option.next;
          if (storyData[nextId]?.isEnd) {
            goToEnd(nextId);
          } else {
            goToStory(nextId);
          }
        };
        optionsBox.appendChild(btn);
      });
    }

    // 进入结局
    function goToEnd(endId) {
      const end = storyData[endId];
      if (!end) return;
      // 隐藏剧情页，显示结局页
      document.getElementById('story-box').style.display = 'none';
      const endBox = document.getElementById('end-box');
      endBox.style.display = 'block';
      // 设置结局标题和内容
      document.getElementById('end-title').innerText = end.title;
      document.getElementById('end-content').innerText = end.content;
      // 重置结局页样式
      endBox.className = `story-box end-box ${end.color}`;
    }

    // 重玩游戏
    function restartGame() {
      // 重置选择轨迹
      choiceTrace = [];
      updateTrace();
      // 显示开始页，隐藏其他
      document.getElementById('start-box').style.display = 'block';
      document.getElementById('story-box').style.display = 'none';
      document.getElementById('end-box').style.display = 'none';
    }

    // 更新选择轨迹
    function updateTrace() {
      const traceList = document.getElementById('trace-list');
      traceList.innerHTML = '';
      choiceTrace.forEach((item, index) => {
        const li = document.createElement('li');
        li.className = 'trace-item';
        li.innerText = `${index + 1}. ${item}`;
        traceList.appendChild(li);
      });
    }

    // 初始化轨迹
    updateTrace();
  </script>
</body>
</html>
