---
title: "18 Claude Code Token Hacks in 18 Minutes"
date: 2026-04-02
creator: nate-herk
youtube: https://youtu.be/49V-5Ock8LU
source_url: https://drive.google.com/drive/folders/1otBAvqeuLexmyNxEIUSnhkcVp2yB5bNb
type: source
concepts:
  - mcp
  - subagents
  - planning-mode
  - token-optimization
  - workflow-automation
entities:
  - claude-code
---

# 18 Claude Code Token Hacks in 18 Minutes

> 18 practical hacks to reduce Claude Code token usage

## Links
- Watch: https://youtu.be/49V-5Ock8LU
- Original source bundle: https://drive.google.com/drive/folders/1otBAvqeuLexmyNxEIUSnhkcVp2yB5bNb
- Raw artefacts: `../../raw/18-claude-code-token-hacks-in-18-minutes/` (1 files)
- Creator: [[nate-herk-profile]]

## Cross-references
**Concepts:** [[mcp]], [[subagents]], [[planning-mode]], [[token-optimization]], [[workflow-automation]]
**Entities:** [[claude-code]]

## Files
- [`Context Management.pdf`](../../raw/18-claude-code-token-hacks-in-18-minutes/Context Management.pdf) — 22476.8 KB

---

## Context Management.pdf
_PDF, 36 pages — [open](../../raw/18-claude-code-token-hacks-in-18-minutes/Context Management.pdf)_

### Page 1

@ A I A u t o m a t io n S o c ie t y 18 Token Management Hacks T i e r 1 T i e r 2 T i e r 3

### Page 2

A toke n is th e sma lle st unit of te xt th a t a n AI mode l re a ds a nd ch a rge s you for, rough ly one toke n pe r word. Eve ry time you se nd a me ssa ge, Cla ude re -re a ds th e e ntire conve rsation from the be ginning. Me ssa ge 1, its re ply, me ssa ge 2, its re ply... a ll th e wa y to your la te st prompt. Eve ry. Single. Time. @ A I A u t o m a t io n S o c ie t y How tokens actually work.

### Page 3

Th is me a ns cost compounds, not a dds. Me ssa ge 1 migh t cost 500 toke ns. Me ssa ge 30 costs 15,000+, be ca use it's re -re a ding e ve ryth ing be fore it. One de ve lope r tra cke d a 100+ me ssa ge ch a t: 98.5% of all toke ns we re spe nt re -re ading old h istory. Only 1.5% we nt towa rd ne w output. @ A I A u t o m a t io n S o c ie t y How tokens actually work.

### Page 4

@ A I A u t o m a t io n S o c ie t y How tokens actually work.

### Page 5

On top of your me ssa ge s, Cla ude a lso re -loa ds your CLAUDE.md file, a ll conne cte d MCP se rve r tool de finitions, syste m prompts, a nd re fe re nce d file s on e ve ry single turn. Th is ove rh e a d is invisible but consta nt. @ A I A u t o m a t io n S o c ie t y How tokens actually work.

### Page 6

Bloate d conte xt doe sn't just cost more, it produce s worse output. Re se arch on th e "lost in th e middle " ph e nome non sh ows mode ls pay le ss atte ntion to conte nt burie d in long conte xts. Ke e ping conte xt tigh t isn't just a cost move. It's a q uality move. @ A I A u t o m a t io n S o c ie t y How tokens actually work.

### Page 7

@ A I A u t o m a t io n S o c ie t y Tier 1 Hacks

### Page 8

@ A I A u t o m a t io n S o c ie t y 1 /9 Use /cle a r be twe e n unre la te d ta sks. Don't ca rry conte xt a bout topic A into a conve rsa tion a bout topic B. Eve ry me ssa ge in a long ch a t is e xpone ntia lly more e xpe nsive th a n th e sa me me ssa ge in a fre sh ch a t. Th is single h a bit is th e # 1 th ing th a t e xte nds se ssion life. Start fresh conversations

### Page 9

@ A I A u t o m a t io n S o c ie t y 2/9 Eve ry conne cte d MCP se rve r loa ds ALL its tool de finitions into your conte xt on EVERY me ssa ge, e ve n if you ne ve r touch it. One se rve r a lone = ~17,600 toke ns pe r me ssa ge. Run /mcp a t th e sta rt of e a ch se ssion. Disconne ct e ve ryth ing you won't use. Use CLIs inste a d! Disconnect MCP servers

### Page 10

@ A I A u t o m a t io n S o c ie t y 3 /9 Th re e se pa ra te me ssa ge s cost 3x wh a t one combine d me ssa ge costs. Inste a d of "summa rize th is" → "now e xtra ct th e issue s" → "now sugge st a fix", se nd it a ll in one prompt. If Cla ude ge ts some th ing sligh tly wrong, e dit your origina l me ssa ge a nd re ge ne ra te inste a d of se nding a follow-up corre ction. Follow-ups sta ck onto h istory pe rma ne ntly. Edits re pla ce th e ba d e xch a nge e ntire ly. Batch prompts into 1 message

### Page 11

@ A I A u t o m a t io n S o c ie t y 4 /9 Cla ude ma ps out its a pproa ch a nd you a pprove be fore it write s a single line. Pre ve nts th e single bigge st source of toke n wa ste: Cla ude going down th e wrong pa th, writing code, th e n ne e ding to undo a nd re do. Add th is to your CLAUDE.md: "Do not ma ke a ny ch a nge s until you h a ve 95% confide nce in wh a t you ne e d to build. Ask me follow-up q ue stions until you re a ch th a t confide nce." Plan Mode before any real task

### Page 12

@ A I A u t o m a t io n S o c ie t y 5/9 /conte xt sh ows you e xa ctly wh a t's e a ting your toke ns righ t now: conve rsa tion h istory size, MCP ove rh e a d, loa de d file s, e ve ryth ing. /cost sh ows your a ctua l toke n usa ge a nd e stima te d spe nd for th e curre nt se ssion. Most pe ople h a ve no ide a wh e re th e ir toke ns a re going. Th e se two comma nds ma ke th e invisible visible. You ca n't fix wh a t you ca n't se e. Run /context and /cost

### Page 13

@ A I A u t o m a t io n S o c ie t y 5/9 Run /context and /cost

### Page 14

@ A I A u t o m a t io n S o c ie t y 6/9 Th is sits in your te rmina l wh ile you work. With out it, you ca n ge t de e p into a coding se ssion, fe e l productive, a nd th e n sudde nly h it a wa ll be ca use you burne d th rough e ve ryth ing with out re a lizing. /sta tusline Set up a status line

### Page 15

@ A I A u t o m a t io n S o c ie t y 7 /9 Keep your dashboard open

### Page 16

@ A I A u t o m a t io n S o c ie t y 8/9 Be fore you drop a docume nt, file, or e rror log into th e ch a t, a sk yourse lf: doe s Cla ude ne e d th e e ntire th ing, or just one se ction? If th e bug is in one function, pa ste th a t function. If th e e rror is in th e la st 10 line s of a log, pa ste th ose 10 line s. Cla ude sh ould be pre cise a bout wh a t it re a ds, a nd you sh ould be pre cise a bout wh a t you fe e d it. Be smart with pasting

### Page 17

@ A I A u t o m a t io n S o c ie t y 9 /9 Don't just fire off a prompt a nd wa lk a wa y. Wa tch wh a t Cla ude is doing, e spe cia lly on longe r ta sks. Some time s it ge ts stuck in its own loops, re -re a ding th e sa me file s, re trying th e sa me a pproa ch, or e xploring pa th s th a t cle a rly a re n't going a nywh e re. Watch Claude work

### Page 18

@ A I A u t o m a t io n S o c ie t y 9 /9 If you se e it doing some th ing unne ce ssa ry, stop it e a rly. Hit Esca pe. You'll sa ve e ve ry toke n it would h a ve burne d finish ing a use le ss loop. Th is ma tte rs more th a n pe ople re a lize. In a ba d loop, 80% + of th e toke ns be ing use d a re producing ze ro va lue. A fe w se conds of a tte ntion ca n sa ve th ousa nds of toke ns. Watch Claude work

### Page 19

@ A I A u t o m a t io n S o c ie t y Tier 2 Hacks

### Page 20

@ A I A u t o m a t io n S o c ie t y 1 /5 Pla ce it in your proje ct root. Cla ude a uto-re a ds it a t th e sta rt of e ve ry ch a t a s syste m conte xt. <200 line s Include: your te ch sta ck, coding conve ntions, build comma nds, th e 95% confide nce rule. Tre a t it like a n inde x. Route to wh e re more da ta live s. Th is is a mindse t sh ift. Lean CLAUDE.md

### Page 21

@ A I A u t o m a t io n S o c ie t y 1 /5 Ke e p it le an and trim ruth le ssly. Eve ry toke n in your CLAUDE.md loa ds on e ve ry single me ssa ge, so a bloa te d one de fe a ts its own purpose. Include only wh a t Cla ude ne e ds to a void e xploring or a sking you a bout. Don't put your proje ct's e ntire h istory or docume nta tion th a t Cla ude ca n find by re a ding source file s wh e n ne e de d. Lean CLAUDE.md

### Page 22

@ A I A u t o m a t io n S o c ie t y 2/5 Don't: "He re 's my wh ole re po, go find th e bug." Do: "Ch e ck th e ve rifyUse r function inside a uth.js." Use @ file na me to point a t spe cific file s inste a d of le tting Cla ude e xplore fre e ly. Be surgical with file references

### Page 23

@ A I A u t o m a t io n S o c ie t y 3 /5 Auto-compa ct trigge rs a t ~95%, by wh ich point your conte xt is a lre a dy de gra de d. Run /conte xt to ch e ck your ca pa city pe rce nta ge. At ~60%, run /compa ct with spe cific instructions on wh a t to pre se rve. Afte r 3-4 compa cts in a row, q ua lity sta rts to de gra de. At th a t point, a sk Cla ude to write a se ssion summa ry a nd /cle a r. Compact at ~60% capacity

### Page 24

@ A I A u t o m a t io n S o c ie t y 4 /5 Cla ude Code use s prompt ca ch ing to a void re -proce ssing unch a nge d conte xt. But th e ca ch e h a s a 5-minute time out. Afte r 5 mins, your ne xt me ssa ge re -proce sse s e ve ryth ing from scra tch a t full cost. Th is is wh y some pe ople fe e l like th e ir usa ge spike s "ra ndomly" a fte r pa using. If you're ste pping a wa y for more th a n a fe w minute s, conside r doing a /compa ct or /cle a r be fore. Short breaks cost you

### Page 25

@ A I A u t o m a t io n S o c ie t y 5/5 Wh e n Cla ude runs sh e ll comma nds, th e full output e nte rs your conte xt window. A git log with 200 commits, a ve rbose te st suite, a build log full of wa rnings... a ll toke ns, a ll re -se nt e ve ry turn a fte r. Be inte ntiona l a bout wh a t you le t Cla ude run. Pipe long outputs th rough h e a d or ta il, or a sk Cla ude to limit output be fore running a comma nd. Command output bloat

### Page 26

@ A I A u t o m a t io n S o c ie t y 5/5 Th is is one of th ose invisible toke n dra ins th a t pe ople ne ve r th ink a bout be ca use th e output scrolls by a nd fe e ls "fre e." It's not. Command output bloat

### Page 27

@ A I A u t o m a t io n S o c ie t y Tier 3 Hacks

### Page 28

@ A I A u t o m a t io n S o c ie t y 1 / 4 Sonne t = your de fa ult for most coding work. Haiku = suba ge nts, forma tting, simple ta sks (3x ch e a pe r th a n Sonne t). Opus = de e p a rch ite ctura l pla nning only, a nd only wh e n Sonne t wa sn't e nough. Ke e p unde r 20% of tota l usa ge. Pick the right model

### Page 29

@ A I A u t o m a t io n S o c ie t y 2/ 4 Age nt workflows use rough ly 7-10x more toke ns th a n a sta nda rd single -a ge nt se ssion. De le ga te to suba ge nts for one off ta sks th a t ca n use Ha iku. Ea ch suba ge nt runs its own full conte xt window a s a se pa ra te Cla ude insta nce. Age nt te a ms? Ve ry e xpe nsive. Cost of subagents

### Page 30

@ A I A u t o m a t io n S o c ie t y 3 / 4 Anth ropic a djuste d h ow fa st your 5-h our se ssion window dra ins ba se d on de ma nd. Pe ak (drains faste r): 8 AM - 2 PM ET on we e kda ys. Off-pe ak (lasts longe r): Afte rnoons, e ve nings, we e ke nds. Run your big re fa ctors, multi-a ge nt se ssions, a nd code ba se re write s in th e e ve nings or on we e ke nds. Understand peak hours

### Page 31

@ A I A u t o m a t io n S o c ie t y 3.5/ 4 If you're ne a r a re se t with room le ft in your a lloca tion, go h e a vy. Run th e big re fa ctor, le t th e a ge nts loose. Ge t your mone y's worth be fore it re se ts a nywa y. If you're ne a r your limit but th e re se t is only 30-45 minute s a wa y, ste p a wa y. Ta ke a wa lk, gra b a sna ck. Come ba ck to a full budge t inste a d of burning th e la st 5% on some th ing sma ll a nd ge tting stuck mid-ta sk. Bonus: Play the clock

### Page 32

@ A I A u t o m a t io n S o c ie t y 4 / 4 Your CLAUDE.md sh ould conta in sta ble de cisions, a rch ite cture rule s, a nd progre ss summa rie s. Th ink of it a s th e source of truth th a t ma ke s e ve ry future prompt sh orte r. Sa ve de cisions, not conve rsa tions. Eve ry a rch ite ctura l ca ll you store th e re is a pa ra gra ph you ne ve r h a ve to type a ga in. Your system's constitution

### Page 33

@ A I A u t o m a t io n S o c ie t y 4 / 4 Add conte xt rule s dire ctly into it, like: "Use suba ge nts for a ny e xplora tion or re se a rch. If a ta sk ne e ds 3+ file s or multi-file a na lysis, spa wn a suba ge nt a nd re turn only summa rize d insigh ts." Th is offloa ds de cision-ma king from your prompts to your config. Your system's constitution

### Page 34

@ A I A u t o m a t io n S o c ie t y 4 / 4 Your system's constitution

### Page 35

@ A I A u t o m a t io n S o c ie t y Your action list: Run /conte xt a nd /cost Sta tus line is sh owing mode l, conte xt %, a nd toke n count Cla ude usa ge da sh boa rd for re ma ining a lloca tion + re se t time Disconne ct unuse d MCP se rve rs via /mcp Sta rt comple x ta sks in Pla n Mode (Sh ift+Ta b) be fore writing code Use /cle a r wh e n switch ing to a n unre la te d ta sk Ma nua lly /compa ct a t ~60% conte xt ca pa city Ba tch multi-ste p instructions into single me ssa ge s Sch e dule h e a vy se ssions for off-pe a k h ours

### Page 36

@ A I A u t o m a t io n S o c ie t y Bottom line Most pe ople don't ne e d a bigge r pla n. Th e y ne e d to stop re -se nding th e ir e ntire conve rsa tion h istory 30 time s wh e n th e y could se nd it 5 time s. It's not a limits proble m. It's a conte xt h ygie ne proble m. Th e Tie r 1 move s a lone will ma ke most pe ople fe e l like th e y double d th e ir subscription.
