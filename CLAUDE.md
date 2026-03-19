# BeatRaft

Interactive single-page Raft consensus tutorial game. Players try (and fail) to break the safety invariant by killing and delaying nodes.

## Structure

Single file app: `index.html` — all HTML, CSS, and JS inline. Deployed on GitHub Pages.

## Raft Implementation

- Single-decree Raft with 3 nodes (Red, Green, Blue)
- Messages: rv (RequestVote), vr (VoteReply), ae (AppendEntries), ar (AppendReply), commit
- Term numbering: Red uses 1,4,7..., Green uses 2,5,8..., Blue uses 3,6,9...
- Message colors in lanes and animations follow the term owner (leader), not the sender

## Game Mechanics

- Double-click: kill/recover a node (only one down at a time)
- Click & hold: delay a node's message processing
- Score: max(0, messages_sent - 5) per round; first 5 are "free" (normal Raft)
- Timeouts (15-25s) trigger new elections when leader is unresponsive
- After consensus, new round auto-starts

## Timing (at 1x speed)

- Message travel: 5000ms
- Process delay: 1500ms
- Leader timeout: 15000-25000ms
- Leader message stagger: 2000ms between sends to each follower
- Round end delay: 6000ms
