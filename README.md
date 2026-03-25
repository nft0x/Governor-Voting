# Governor-Voting
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v5.0.0/contracts/governance/Governor.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v5.0.0/contracts/governance/extensions/GovernorVotingSimple.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v5.0.0/contracts/governance/extensions/GovernorCountsVotes.sol";

contract BaseGovernor is Governor, GovernorVotingSimple, GovernorCountsVotes {
    constructor() Governor("BaseGovernor") {}

    function quorum(uint256) public pure override returns (uint256) {
        return 1000 * 10**18; // ví dụ quorum
    }

    function votingDelay() public pure override returns (uint256) {
        return 1; // blocks
    }

    function votingPeriod() public pure override returns (uint256) {
        return 100; // blocks
    }
}
