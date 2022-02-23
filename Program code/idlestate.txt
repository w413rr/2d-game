using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class IdleBehaviour : StateMachineBehaviour
{
    Override public void OnsatteEnter(Animator animator, AnimatorStateInfo stateInfo, int layerIndex)
    {
        CombatManager.instance.canReceiveInput = true;
    }

    override public void OnstateUpdate(Animator animator, AnimatorStateInfo stateInfo, int layerIndex)
    {
        if (CombatManager.instance.inputReceived)
        {
            animator.SetTrigger("AttackTwo");
            CombatManager.instance.InputManager();
            CombatManager.instance.inputReceived = false;
        }
    }
}
