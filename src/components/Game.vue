<template>
  <div>
    <div class="col">
      <button @click="start()" class="btn btn-primary mr-5 mb-4">Start</button>
      <button v-bind:disabled="end" @click="attack()" class="btn btn-warning mr-2 mb-4">Attack</button>
      <button
        v-bind:disabled="end"
        @click="specialattack()"
        class="btn btn-danger mr-5 mb-4"
      >Special Attack</button>
      <button @click="reset()" class="btn btn-light mb-4">Reset</button>
    </div>

    <div class="row">
      <div class="col-6 alert alert-danger" role="alert">
        <h5>Player : {{aPlayer.name}}, HP : {{aPlayer.hp}}</h5>
      </div>
      <div class="col-6 alert alert-danger" role="alert">
        <h5>Monster : {{aMonster.name}}, HP : {{aMonster.hp}}</h5>
      </div>
    </div>

    <div class="row">
      <div class="col-5">
        <br />
        <div style="position: absolute; z-index: 2;">
          <img style="width:100%" :src="aPlayer.img" />
        </div>
      </div>

      <div class="col-2">
        <br />
        <div v-if="aMonster.hp <=0 ">
          <br /><br /><br /><br /><br />
          <img
            src="https://lh3.googleusercontent.com/REIMRDp9r50VywqEqFaeaWzpP1tsBCjDTuoLnZyPHxCDU9JXfMB535tBsxvrqiTUhPAFF_60AczxEWvE3BapsZY0vhyj6Kp9uvOh5OuopXf03lH5YQdqR6wlq9L1LxcHKiD0LqdO61a29ivULMf-sd6VZhtVvyPhYhJu58FU5VphDkuiUE2wUDLbyX2VN50oB9p38TgFxWb0jVYr6Ivm6sfYfNFhq7g0RMrSLfno-IZ1MVjrjox3aDzuRntL27yXqk2J-B0apTo6ec0KySlUyc0vqzLfGjTQzF2tG4zv5iNDLi_qX_thb_2vPN8lLddZoEj-Mhqexv0fW--QsdSQS6pyx8zmJ6RhRp9OfudkNeXJk5dT5--6nBxdToe88b-X5OZsW6jjZpHoEXgyz6X8pNgl-oO68OdwN4WNQse1q5Itx02o0UCOAOpNdf-bNJJw-zByiePTBIU_1Qmxiehw6AGn-NZ9_S6vbzpoZXZkYsBEhK81DcqO80bbFb2NycFC74rF24cnF2jKEa6wmXRRa1ClFTHh4NumEKbdomfhiucHkP5EiD29p72eG6OS3UvUhBOhovinvaCf7MHR54Vsf4bI1907SOTKjiZPXN0l6_6ldnOS-kDaGi2VYP06DzeZbnrWICW8IzMod8tLtpMEwYbkKeRvOoJ5BHdFC72UUQ3Wi37L-pohHM3gY2vcdQ=w408-h576-no?authuser=0"
            width="100%"
          />
        </div>
        <div v-else-if="aPlayer.hp <= 0 ">
          <br /><br /><br /><br /> <br />
          <img
            src="https://lh3.googleusercontent.com/dkwrKjK9mFd0hFRWZsYimQaGSdGKrt_FWI5O4nVmTpFob4XY68bAW-vXP4KsmeDGoXV_fWYA9Eo0moK8ghPRh36MUtG6A4KkruXBe-gVXJK8YYXAtgkAV-jO2-fZe34Im2h7i5DTN2wZXCQB3LnvUlAz-q9GoGN_MUXb-ixNQqMv0Et6NT08Fk8QyWsYySilsMDQQzaHTCQmvD9_NRKg0GwzQ35LUHnidrl9kijhpud5q4UD8X1gKCkoMIai177NiWMQDO7FG7soA7uPrn_nlv0_vv2NQNyBhh5-kd3qrEvyatOaxgrW2XpOKyzxUI5c-38yQzCDW7CRTiij0SkEwgIOZLnX-SzksV-KxtR1MTp_bp8nf9yov15mqcuK68RS2RpCR_i_6ItH_cUlx5d5yL8BgNIr5tr18ghUtqq43S53rV4QhrmmIkpze8GFW7QFcUoJ8yEzmTGE1R1OMgJhdsx3eqN4GHP4w5AjOHlfQUZlCHzkSoxjY-CkwFagMMCehlmU2ORdE2ktF9qQRMVb8oEId1VrPHLVMnH2w3-pAqDntXHluMb_GKdVKZzabR9s2G4pyH0q-sAImOP0VexcZDJLsTbG2_TOEEBCtHy0Ii9bKUeKN2V2LsU1Zcmubd8v2ycrKZ_Y9lrxcJ5bOnIIhyMLwFdNOItARYSwO6YcsgWj25uKn6lbCTQv50LgIA=w408-h576-no?authuser=0"
            width="100%"
          />
        </div>
        <br /><br /><br /><br /><br /><br />
        <img
          src="https://lh3.googleusercontent.com/WzlLSbhKO8cCD_TBSN0AO3iVgMep922LwYk3FR010C7xFYdJtUaPXoaGZE-46T-R1vFNNr9HjwQif7HYhCA-tnNA8W0a6WP-rHpNhhe6dCchIaNzt8hDSaZL_M6d9LdNLc5kWdfNzqRHWNG6LppxT7wwNvdakAOpXQjxaiooPX7RFtyMHwwMVuy_2aR-hhNAzrKeXQNjAleygAHAzt9UgMlnMIuGCg_vwZCRbZWwJ1hGEL8zCrOXhTI7L_O4O-yqfG2cPSMkIjDFWEqarKYEJXz0wx8y9Fi4tIy-ZTnuDcUVPHqzoF6aa7D-lSwZO-3mKeCdB0lbYXm3IarzlhTE5fR7oShF9Zf-rW5khPX0iNh44vGKg-yx3_8_uB7zU_xzhAUCN1nRzIb7YP9jrMSDt-_I7Rh-ouZMh56mfVKTQJZnoIsBUfawz0nnmGZ6qdqFyr3dxy-5gNfzOdy4OV771uRhdvQOKA5uPiqniL2StMu_Cp7KV7MU1l_hNOyVJUOlhWTDYr9HhWb3a7sxehZwudx6bI5sWiglN3YQQgbN7mSOCcOh_cwDccJhiJHqeVuMHPAOoTi0M005Xfad-eoSiUkd8lqMqV5XBn0hhDkX_WiOsapgaGccHOmzveIzdiY-6jVEpT9WfsVOfgN9X4Pf3SUlAd0OaqNNFAe8pWw1aezMd2rxmE5VBatQgUoADw=w408-h576-no?authuser=0"
          width="80%"
        />
      </div>

      <div class="col-5">
        <div style="position: absolute; z-index: 4;">
          <img style="width:100%" :src="aMonster.img" />
        </div>
      </div>
    </div>
    <br /><br /><br /><br />
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      vs1: "",
      playmax: "",
      monsmax: "",
      end: false,
      aPlayer: { name: "", hp: 1, img: "", hp1: "" },

      player: [
        {
          name: "Yuta",
          hp: 500,
          img:"https://photos.app.goo.gl/w7PaxSiaJqin3DSj8",
        },
        {
          name: "Saito",
          hp: 450,
          img:"https://lh3.googleusercontent.com/P9gOXtnyoFxOYYN1dVn44WPwZKBACZ1EDX19lNBvLNHvetWovBctbgThr0vdsLa_bgFGLuiX--0Igp2MI2VwsgrVwS5Qxixb3XvXOlB7KuxnI309HHGrUdjuYZWAId__iYjDlrDkt-q9du4De901fax1u2FDwbnp6uMyE0sCQXXw3tc6MgIbZYWvujxTnbrqORA8SQFpwe7gw85XQ9AUJa_jdaz2_pBje-hFK6eHmPa6kPTn7FVuSDYh9HWhsvGYFcbv8WgwL_xxuh8WYOwuZHZD2lkWngXkZycJkXH2Qy76doejk_ZIyCUjo5ckep9HlZdN4Lo2jR2E8uQOIfCyAbjyKfQrQVbhXQp75cd72j8QmTY1dlbVPIXhBg5dPSTORC3nv4eCiHvZknYePYAMkZ2MiazZF-WVrmnts9XP1x5BqIbMjLugYG6eEWCqEnVzVtkkFzct3OMIeyLNfewBJz7aZNF7N90fDs45YQzeNIh_QJatcgHNuQUz9ZcCVHebJDgJjaLlYvhjUTB7LYKpBT4M2Pei0i9OpuJ4C1NpPPHvElu2Z6TBfQ4CZ8cddVR14ddUQDepAxL_HjNcIWceKR8GEiHjP4E2-04tiQNUROrIH5FuoomXW4-EL_RETquCpmyLCAyvig6BoLmxz3A5I-of0-t_oWjiERfqGzCN25OSy1KOpXSnzUvAS1rl7w=w442-h625-no?authuser=0",
        },
        {
          name: "Kyoshin",
          hp: 350,
          img:"https://lh3.googleusercontent.com/SgydC6NuwBJy9MuA8W_p1Fg2W-gJ3z3C0yufRnYEK14899AWGkgz0iCzJrtI1pfPCqJSN1MNrZA7FlzTB50-zTrn_qNWQLUzNTVaxxnfmk0iRGmjjN6AMpVbpw11vIkv6G3z1npDlUrtV51h6am1fYAW551h6ocxHyrIl-S7HewztNEwF8XLVrmlvE3U-jxxGXPNuSkBz_ByFugXmc3H9ON9z9kAHao1rzeMxYtFIArhx0pavYcUxZyacYpTfxajgjP4y2oHhh3kiiLTh7FYOOnyhzRqaU7YzzaAfschtSz-hdz520Fw8ZTw5eDJCPaSiqDHAlU9OZzxuCIA6odk4ezLoeD7QB8-GI2GYIAX4RVdAWbobVWU5Pw8G838N8fauDMPHbWGZgN34m7tMteoPFczAPfYH0wSWCbKTbpnoZenjLgQQjCcbyDUPcpc5OTvF27kPnBFjLil5ZxlWnLSBWhhj3VYL8t2QoadT16eWPaDPO9cxz-pEJGy7k_5eBLqYpPj8Xy_dZUUcQc4NY5W_RwtB_OKvjTck6S-kTVWX1-XvLemR6yXcAJfloNpkU9rdCFxeQcvpneIGl-LDjoeKdbPi2Q2QLknERa0wFMttNsSDJO_E1RToZ-AR34Gyyg1DN5zI3yVAOB4vZdZMpwQSQhUPwAJCeS_CwCLzhr5DSpW4CsA0YRPK4Z5BMRDtQ=w442-h625-no?authuser=0",
        },
        {
          name: "ํYukari",
          hp: 300,
          img:"https://lh3.googleusercontent.com/jfrnGrzgim1Ika9Rd6J8ARosl7R89opPHWq0nGSyAtWMfknvZozyHB4CuJtteyHX-_VZKEQ0UDhA4gs8qGlK4Au1GjX_vWeZJDac5SEFh_h3abhHpVbbbRT5wx5bnCqYQfT649lk7Nm24NfJnBUoUXVWBLJord5kuQsFjT07uY7Nf9xawgxpDk2uww99_IjNplDuJr39eYXlRqeimpk05Uh_72BMWChMGiSnOPUjb2El1H2Zj9EiJ1Sh4-WkVd41wrFJMtJAENDOdBm231iJUZNZ9y2SJDIHEJSUZb-fbgWuZxn5ld2Q0-kqh2TnqDvYC01jPKOi5ogVkhl3hh65rVyO27Y4fi3ROCCNpZli6UtAMRFLGeCueOwuVtpzZbvL9Br9UO3vZdoV64t6u1PPyqQCr_WBIkrg7KE5iCt12k7gj5EaZbiHbX1m8O8tqpNTdykXEagI2LLAEMSu43bo9s833yEu6hYYoMhUJTdmkHK2JwFekXuTpIB63MfOMxUSZp8WU5JwRGRGfgRAHWmKtmVj6xKGpHjpKdx3nu0-aH58yl5R05ShMwH8zKsTlissgJbVJou34u2qfdhA7rfquIi-Ch1KoV2gN0CMl2hTDc9ZdKGAWZwcOk_ONwva8W3LI187uKnLCnTrbfgRWzrvakgVLjwm8V7HHH4-YWdbpN6ioMzQQ-0fFVECl5pgXg=w442-h625-no?authuser=0",
        },
        {
          name: "Saya",
          hp: 250,
          img:"https://lh3.googleusercontent.com/hBiX9KPgkDFLiHh3lbMwcxNJw37coeRa4RiTWcHLKNnPGzdWnIYLx1XrpuhRcuX4hkinQX_R1jW3nAgGUUQz3LZfCK_abi5RwY-erTmEtCmiUTJJuyQ5V1jQXI7RBmxnL87GMqRwETcoXueR-tRjSk9iCsOzwTOVo9_V4utCzhRXyNqCU7eGC9mObpNqCRt0oAtlRi6ZK15M3JRi0F-mo7_EA6A5D23b2AvFRS88yc1sXBoWIWIF0fto2Db64jMr6ue8E3fMm3t27Fyjtoijs-kleA03VHoi0cI_Yrc5leEiPaijf42J6AIl7puyK45jDucPrtlKK4Jj5FTt4KUj2BhuYJvU9sznB4n5_Y7hSZCbR02qd0PtwPU4QWqOGC_hx21Fv-BMa9fX7jO-ipoXFoOEMbejWF2Fda-OgvxqGx4pwmtDXmj9JXZVb6hmyLlZ-8GFP67KQCC-wb5T3lYIIkpVjY1koDbpuLMPzPNaSdhgl7rC0Z7vDZUgUAV-U4wOudCaw9UEsWC_MhJv0fRXpuiYRMcLFmdFDD6t-Z2BGerpjQqggcs6V7W8M_G88Xtp75CYDI7Nji8hf_G0GRykmP4kU5kPgEj4tUe2e6D9U3zKDesrcRRQrA2GOWFLFGF6EJG84PLKPWxigjM1L_BO3Kp-SdEdmxv7XY8hlD6sUNG7xoo-ngPaPmdGH_NLYw=w442-h625-no?authuser=0",
        },
      ],
      aMonster: { name: "", hp: 1, img: "", hp2: "" },
      monster: [
        {
          name: "Yoshitaka",
          hp: 480,
          img:"https://lh3.googleusercontent.com/-x_UoproHtAn9JQBhCaN7219DzSnUSukwryAyq52tOu8dChXhIJdZNTnZH87ngXndEnwR_eEznhEsHnmjoQxeOQl3vSrh068NsE1mitpvUduSXY3XyT2nkq29ct3qKWWbBmlQTTVF8gKfZ7CZW4c1PUousDoKzM3XHdyZt8Q3Y6fY_IStzO4bl9L0EbuEz6Sy8gTtLEIhC93wI4offoaex2I2WcqMMOvkWUBuBczVgpGz-Pza6o3sE-Wz0RZib8bTzLnDKtWRjeSQXdotN37PYf53u2TzgBeHSGNEB_T1hXqO8V4mPmQqb9vML6QzC8VktInkYkeRJEA4M7ukYX1A4fIS2JjSae9nkbUkxb2AtjYsHFJdudhtXMvtgtTRqd8HSkLMHuC5QKamLfzvb8_n8uN3gkWS_YHYxxz8Ysv-USN5ZD8YNpk7OZjcnTI5mbAAr4wrvLMTDpLVDQv-jRzmksfGo2UeOl9lIPX3RmF1EifzsFfOjz8upWwlUU-7Jr33Ro50RM-yaVTM5THWgunNIXDeD-xuisYTg4bg5FGa-A6vz1CJMK6K8eBUxao1YVRIpNG7paHFl3MzQqCNl1wZvLXnL42Dv6a7JihtAkKO6IiL8w-TNW2x2azqnCRtsxpLzaY6RlKLB2KfYN9xPZDZNhjNXlcoBuwxFCMvMkTh7esMAflDnbDsQ2gAExTuw=w442-h625-no?authuser=0",
        },
        {
          name: "Sugiyama",
          hp: 430,
          img:"https://lh3.googleusercontent.com/DU9abCpRN7TDo_14Ijhf1tToJmyNLnmUnwLoaqt5XVRHBUN_Pb-ezu61pE3QGeuI-Px2pT4uidxrGMjtyTn_a7R7KY8QDrhtqF71N7ASaLgtw2-qzVx-upgNGGoQKgAOIKPfc5PEIdR767I8yEKVNCmoZbOdy-3Z7b6APXXOkWXBMtrLM7OE1YCkm2uYc-qCxAO4nesN_FXa0KFj8EA7IwLIc6OX08TDG017ZMQ3D1_UWo3tpZ0BrwGe6Ps8wztQ2JRT6WZ31w0FYVaCUtiHaiyfAjmTMSeG2BZ1z-DBn5ZkEIh3R9N6-k6-ezBant91iXc3JHUZMCDkgEnzQBHjCKxKM184TOMJm2UXwdirn8IKcY5-XE6FevS5SuymPnVqZNxVnL61DaBl9fxvFBG0A5Q9Dh4lIf9A2QS1sfQnfUiPvl9mx9drRiTrj_5y-TwONqQ1BG9B-VQNA9S2wYNW0CDo5GaWL9Aw9hACHpLuc5yz95lCzjgmhN9z1MVTTcQI9NTmx4wJjcR8dFcHfcG4krhYkOM0zKe-41OLt7cSRk1djtTO2p69B-WxibgEElC0VUjc69Gdklg2e7IVlju8NFubnXXKnrA7qHA8HVy918OHMYCldoZLfX6AxW4zcReKIgfZHH0LCvPzOqM9nHJJuBrX6GzHZq0er9DMXgyH3xwxuRJIH9JiJbsHYrgnZA=w442-h625-no?authuser=0",
        },
        {
          name: "Nakahara",
          hp: 320,
          img:"https://lh3.googleusercontent.com/0xCwfrvQKznShbh1qF32IV7sGOFV7QWh72ScEbmod2mO9cjn5dUjBy5xE1T8TaeJIyGL6jwhr2RWAVgl62DZacdOh2AmZSDu5lA0FgGaYSg129XW2oknpUEyF-5xsQltlsfuTerieJBrRjmC3HCOOUvaPK-qEn-PAJD0wfAsU4vR-hyWQ75b0ELMfcOnk5MMT8LnalJTSVsxbwLGSRS1Ep7ee8KkTLSRaRUu53X9uEk9CKFY4EFzXCyYxLuRYC7WXsLYJRJXe_LXCJ5tjwifFMRIWDQxoXIcjfFQZ3jp4tMyXhK9qr10yyfVP3OZBmm5t836ZhyjyQqesChhBe4MZBvZYMiDClv1AlbNpwJxvnQQRJTpp_tk2sZN1SjIbQRF-IeuzdxYM7qSP7OjeSMQrGl3F0k3Hk2FfxFaeVyeHlvpYFJD_AC4Ch-pKb5JSYNdrOqWPmtzlkXIZHi1G8uvSs2xJq8A2FSCxa8wK4v0G1KX-eMDfGnmOIOfmH0yk-1rDJfIEtJRdnlK22oO4hHA0u23KsAcjiRSTqXQA6oh-k01FarGgSXhxWneAts4qDEXtqcV-cpOvmiKn19PF8beYlqRi5HwKQyGp-7xA6VidKz5K3DV0PPS8K-oASLTPQhPqzpTcZo6QP9Nz_NEEEUnOC0B_U_WW71kJQ9v5dCDddvBfuLzJiqFIM_ZZIZKvQ=w442-h625-no?authuser=0",
        },
        {
          name: "Okazaki",
          hp: 240,
          img:"https://lh3.googleusercontent.com/fCNKiTOH9qavHDwHcKC8RZNYfOXelPuSYt32AK9Z-O1jjVO914jQGV3iLWI1ldK8b7ALAYzE5G2WRP_-R3lDxVt6lRzQFmfzgjp0dZz1gap4GYkj9ePf_hiChqQuXNvNoEMCDj5xiTgevkzBhodalTqSYknk85rAiZmjNhrPGX7iZJ_UTso5s8m8SpvgEmTQTWExHIbo9zKQ1fnJHIUMeoFA5jEfp18BdTuN249eH4uDieE0cGkpEYGbPC1xQttDmLgvSzjUKDk9izTUo38oMK7HJEcn6hpZlVXKIwfbQt2s8A93GXnm5xNfNhdt7CweIzJwvrz_oLd_hR26ZpZN16KXX1meguitkvdcNc2ZULLWpAAPre9eZjgD2ulaKJqCQNYm8WLM3p38_uWryzJLR8hSDA7JJB4kmbNSkeQmwAk4iJelYQ5bC0pgQguzu0lAOLbRlze-PDvKWHMrHmc8AaB7wsv2_yNMIvI1vYfuKQFJ1Zi7HD9-RU8y8GiA-GsQ_6Xn3dEt6Fg6OcDNXpPVMsVHIxB3r_YoXyy-fDyGMi-pDXn7-tT8SQPGrUVJMLLlv1GAR3BBVJ-wrVI4CqHccgqBiYsFquDorWbr1Z26eNlQrVv_DRIwoq2WAVnt2G1NyOyXF6LHYIEaIIN7JDTJgtfDD0XOtQbz_jxtxlHA-pteCi_iUfbFztssTE1Eiw=w442-h625-no?authuser=0",
        },
        {
          name: "Igaarashi",
          hp: 220,
          img:"https://lh3.googleusercontent.com/OxJzsASipzj2PjVhbGRK_mI-dqtqSKTu-VESezvCIBvJ3fA-AnmaJqAsHFNDjFaycXX63dXEFnVQ9EOgutilGW0ogKGcR_VId2JpZ69eP5sclrug6xCa3RzyrGwjUrX5bhaqZWyb0mB59XLXHPq6t6jGrEdUvUcFZV1eyOxK4g3PdyYgTFCJGDgbT-hnnj8HA-mYY7D8ode4DfLTZnKYrNagVzalhiFcCIEUEYoRMNIsOrUtv4m_UKPxi1krgcQ3MfmM-RaIsjyjgLkRUB2QSCAVzumzj2HhZraz2utwTaWagOZSUU-Sdi9WcA66xwbkn2_oWvJNIIy35_l-mUvnIFncC3Tmh_wva6O-qhzQrl05AsLPpfKawKmdMZ9KXEygORnQWxxHvJZHtg9d00FMfyFb6BycX9UimmgPGyWz6edIRm7wbuFSH_NUxXR_REMHfk9Wuz50TUo3ssEod0slUI4QkjEjI-jP3Jd-gIVxcbz82QtHuUowIlAgLGPrvYYKycq9CxKDUzUPBEya8FPYKSJgEFq5h3juFCu3kRQoeDP7ilR28zzRC-7iBHtMeQ7cVL8xs1hh6_ZaONLKt4DAeacGdRSapRjTTubgAvc0Q3_KSH40llEBgkbGql5jbCUut6l8WwOQyFWVE7D7e76F7BX_6hmhcjgSRG1_Hve3-Wkxow7rVbqB_sTAu7I27A=w442-h625-no?authuser=0",
        },
      ],
    };
  },
  methods: {
    random: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },

    start: function () {
      this.aPlayer = this.player[this.random(1, 5) - 1];
      this.aMonster = this.monster[this.random(1, 5) - 1];
    },
    attack: function () {
      this.playmax = Math.floor(Math.random() * 15 + 5);
      this.aPlayer.hp = this.aPlayer.hp - this.playmax;
      this.monsmax = Math.floor(Math.random() * 15 + 5);
      this.aMonster.hp = this.aMonster.hp - this.monsmax;
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp <= 0;
        this.end = true;
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp <= 0;
        this.end = true;
      }
    },
    specialattack: function () {
      this.playmax = Math.floor(Math.random() * 30 + 5);
      this.aPlayer.hp = this.aPlayer.hp - this.playmax;
      this.monsmax = Math.floor(Math.random() * 30 + 5);
      this.aMonster.hp = this.aMonster.hp - this.monsmax;
      if (this.aPlayer.hp <= 0) {
        this.aPlayer.hp = 0;
        this.end = true;
      } else if (this.aMonster.hp <= 0) {
        this.aMonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>

